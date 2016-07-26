---
layout: post
title: "StackExchange.Exceptional 使用步骤"
date: 2016-07-26 15:41:51 +0800
description: ""
category: 
tags: []
---

## 步骤1： 安装包
    
`Install-Package StackExchange.Exceptional`

## 步骤2： web.config 配置

    <configuration>
        <configSections>
            <section name="Exceptional" type="StackExchange.Exceptional.Settings, StackExchange.Exceptional"/>
        </configSections>
        <Exceptional applicationName="Core">
            <IgnoreErrors>
                <!-- 忽略的异常信息（可选） Error messages to ignore (optional) -->
                <Regexes>
                    <add name="connection suuuuuuuucks" pattern="Request timed out\.$" />
                </Regexes>
                <!-- 忽略的异常类型（可选） Error types to ignore, e.g. <add type="System.Exception" /> or -->
                <Types>
                <add type="MyNameSpace.MyException" />
                </Types>
            </IgnoreErrors>
            <!-- 异常存储方式（临时（内存）, JSON文件, SQL数据库  Error log store to use -->
            <ErrorStore type="Memory" />
            <!--<ErrorStore type="JSON" path="~\Errors" size="200" rollupSeconds="300" />-->
            <!--<ErrorStore type="SQL" connectionString="Data Source=.;Initial Catalog=Exceptions;Uid=Exceptions;Pwd=iloveerrors" />-->
        </Exceptional>
        <system.webServer>
            <modules>
            <add name="ErrorStore" type="StackExchange.Exceptional.ExceptionalModule, StackExchange.Exceptional" />
            </modules>
        </system.webServer>
    </configuration>

## 步骤3：增加异常查看页面

    [RoutePrefix("Exceptional"), Route("{action=index}/{resource?}/{subResource?}")]
    public class ExceptionalPageController : Controller
    {
        // GET: Home
        public ActionResult Index()
        {
            var context = System.Web.HttpContext.Current;
            var page = new HandlerFactory().GetHandler(context, Request.RequestType, Request.Url.ToString(), Request.PathInfo);
            page.ProcessRequest(context);

            return null;
        }
    }

## 步骤4：增加页面样式和脚本（Global.asax）

    ErrorStore.AddCSSInclude("~/Content/exceptional/site.css");
    ErrorStore.AddJSInclude("~/Content/errors.js");
    ErrorStore.jQueryURL = "~/Scripts/jquery-2.2.0.min.js";

## 步骤5：如果自定义显示页面，步骤3、4可跳过

- 可以选择存储方式 sql 或 json

- sql 刷库脚本，数据库名称自定义

        CREATE TABLE [dbo].[Exceptions](
            [Id] [bigint] NOT NULL IDENTITY,
            [GUID] [uniqueidentifier] NOT NULL,
            [ApplicationName] [nvarchar](50) NOT NULL,
            [MachineName] [nvarchar](50) NOT NULL,
            [CreationDate] [datetime] NOT NULL,
            [Type] [nvarchar](100) NOT NULL,
            [IsProtected] [bit] NOT NULL default(0),
            [Host] [nvarchar](100) NULL,
            [Url] [nvarchar](500) NULL,
            [HTTPMethod] [nvarchar](10) NULL,
            [IPAddress] [varchar](40) NULL,
            [Source] [nvarchar](100) NULL,
            [Message] [nvarchar](1000) NULL,
            [Detail] [nvarchar](max) NULL,	
            [StatusCode] [int] NULL,
            [SQL] [nvarchar](max) NULL,
            [DeletionDate] [datetime] NULL,
            [FullJson] [nvarchar](max) NULL,
            [ErrorHash] [int] NULL,
            [DuplicateCount] [int] NOT NULL default(1)
        CONSTRAINT [PK_Exceptions] PRIMARY KEY CLUSTERED ([Id] ASC)
        WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
        )

        CREATE UNIQUE NONCLUSTERED INDEX [IX_Exceptions_GUID_ApplicationName_DeletionDate_CreationDate] ON [dbo].[Exceptions] 
        (
            [GUID] ASC,
            [ApplicationName] ASC,
            [DeletionDate] ASC,
            [CreationDate] DESC
        )

        CREATE NONCLUSTERED INDEX [IX_Exceptions_ErrorHash_ApplicationName_CreationDate_DeletionDate] ON [dbo].[Exceptions] 
        (
            [ErrorHash] ASC,
            [ApplicationName] ASC,
            [CreationDate] DESC,
            [DeletionDate] ASC
        )

        CREATE NONCLUSTERED INDEX [IX_Exceptions_ApplicationName_DeletionDate_CreationDate_Filtered] ON [dbo].[Exceptions] 
        (
            [ApplicationName] ASC,
            [DeletionDate] ASC,
            [CreationDate] DESC
        )
        WHERE DeletionDate Is Null

- 获取所有异常方法

        static void DisplayExceptionStats()
        {
            System.Console.WriteLine(ErrorStore.Default.Name + " for " + ErrorStore.Default.Name);
            var count = ErrorStore.Default.GetCount();
            System.Console.WriteLine("Exceptions in the log: " + count);

            var errors = new List<Error>(); //所有异常信息
            ErrorStore.Default.GetAll(errors);

            if (!errors.Any()) return;

            var last = errors.First();
            System.Console.WriteLine("Latest: " + last.Message + " on " + last.CreationDate);
        }

## 步骤6： （可选）自定义(存储/写入)异常

- 代码方式自定义设置存储方式

        ErrorStore.Setup("Samples.Console", new JSONErrorStore(path: "Errors", rollupSeconds: 0));

- 自定写入异常

        ErrorStore.LogException(e, HttpContext.Current); //web
        ErrorStore.LogExceptionWithoutContext(ex);


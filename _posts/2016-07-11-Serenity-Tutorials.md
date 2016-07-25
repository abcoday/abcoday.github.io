---
layout: post
title: "Serenity 教程"
date: 2016-07-22 14:01:51 +0800
description: "Serenity 常用技巧"
category: 
tags: []
---

## 整体框架结构

> 模块

- Modules 模块目录

- Modules/Administration 用户和权限设置模块

- Modules/Common 通用设置模块

- Modules/xxx 自定义模块

> 文件

- [xxx]Dialog.ts //前端弹窗设置

- [xxx]Grid.ts //前端列表设置

- [xxx]Row.cs //数据字段

- [xxx]Columns.cs //可自定义列表呈现的数据字段

- [xxx]Form.cs //可自定义编辑页面显示的数据字段

- [xxx]Page.cs //MVC入口Controller设置及菜单配置

- [xxx]Endpoint.cs //ajax请求服务端API方法

- [xxx]Repository.cs //与DB交换的方法

## 使用sergen命令打开代码生成器

    视图 > 其他窗口 > 程序包管理器控制台  输入`sergen`回车

## 增加菜单配置

    在当前项目 `Modules/Common/Navigation/NavigationItems.cs` 可配置名称、图标、排序

    图标名称参考地址 <http://thesabbir.github.io/simple-line-icons/>

## 列表搜索设置

- 搜索过滤，在字段上增加属性 `QuickSearch` 例如：

        namespace MovieTutorial.MovieDB.Entities
        {
            //...
            public sealed class MovieRow : Row, IIdRow, INameRow
            {
                //...
                [DisplayName("Title"), Size(200), NotNull, QuickSearch]
                public String Title
                {
                    get { return Fields.Title[this]; }
                    set { Fields.Title[this] = value; }
                }
            }
        }

- 条件过滤，在字段上增加属性 `QuickFilter`

## 查找脚本(LookupScript)

- 属性设置`[LookupScript("key")]`  key：脚本调用的名称 例如：

        [LookupScript("EmotionManagement.Category")]
        public sealed class CategoryRow : Row, IIdRow, INameRow

- 脚本调用方法 `Q.getLookup('key')`

- 字段编辑关联 `[LookupEditor(typeof(class))]` class：被设置LookupScript的类 例如：

        [DisplayName("Category")]
        [LookupEditor(typeof(CategoryRow), InplaceAdd = true)]
        public Int32? CategoryId
        {
            get { return Fields.CategoryId[this]; }
            set { Fields.CategoryId[this] = value; }
        }

## 一对多表关联设置(LinkingSetRelation) 例如：

    [LinkingSetRelation(typeof(EmotionPackageMapsRow), "EmotionID", "EmotionsPackageID")]
    public List<Int64> PackageList
    {
        get { return Fields.PackageList[this]; }
        set { Fields.PackageList[this] = value; }
    }

## 自定义列表检索数据

- 创建类继承 `ListRequest` 在该类下创建自定义检索属性 例如：

        public class EmotionsListRequest : ListRequest
        {
            public List<int> Packages { get; set; }
        }

- xxxGrid.ts 文件下 赋值自定义检索的值 例如：

        protected getQuickFilters() {
            let items = super.getQuickFilters();
            var packageListFilter = Q.first(items, x => x.field == EmotionsRow.Fields.PackageList);

            packageListFilter.handler = h => {
                var request = (h.request as EmotionsListRequest);
                var values = (h.widget as Serenity.LookupEditor).values;
                request.Packages = values.map(x => parseInt(x, 10));
                h.handled = true;
            };

            return items;
        }

- xxxRepository.cs/xxxEndpoint.cs 使用新类,  文件下过滤数据结果 例如：

        private class MyListHandler : ListRequestHandler<MyRow, EmotionsListRequest>
        {

            protected override void ApplyFilters(SqlQuery query)
            {
                base.ApplyFilters(query);

                if (!Request.Packages.IsEmptyOrNull())
                {
                    var epm = Entities.EmotionPackageMapsRow.Fields.As("epm");
                    query.Where(Criteria.Exists(
                        query.SubQuery().From(epm)
                        .Select("1")
                        .Where(epm.EmotionId == fld.EmotionId && epm.EmotionsPackageId.In(Request.Packages)).ToString()

                        ));
                }
            }

        }












---
layout: post
title: "移动端web开发技巧"
date: 2016-03-01 17:51:58 +0800
description: "移动端web开发技巧"
category: 
tags: []
---



<div class="detail-content-wrap">
    <h1 class="detail-title">移动端web开发技巧</h1>
    
    <div class="detail-content ">
        <blockquote>
            <p>这是一个最好的时代，因为我们站在潮流中；但也是一个最坏的时代，因为我们站在潮头上。</p>
        </blockquote>
        <strong style="display:block;font-size:22px;margin:22px 0 10px"><strong>META相关</strong></strong>
        <p><strong>1. 添加到主屏后的标题（IOS）</strong></p>
<pre class="prettyprint"><code><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"apple-mobile-web-app-title"</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"标题"</span><span class="tag">&gt;</span><span class="pln"> </span></code></pre>
        <p><strong>2. 启用 WebApp 全屏模式（IOS）</strong></p>
        <p>当网站添加到主屏幕后再点击进行启动时，可隐藏地址栏（从浏览器跳转或输入链接进入并没有此效果）</p>
<pre class="prettyprint"><code><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"apple-mobile-web-app-capable"</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"yes"</span><span class="pln"> </span><span class="tag">/&gt;</span><span class="pln"> 
</span><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"apple-touch-fullscreen"</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"yes"</span><span class="pln"> </span><span class="tag">/&gt;</span><span class="pln"> </span></code></pre>
        <p><strong>3. 百度禁止转码</strong></p>
        <p>通过百度手机打开网页时，百度可能会对你的网页进行转码，往你页面贴上它的广告，非常之恶心。不过我们可以通过这个meta标签来禁止它：</p>
<pre class="prettyprint"><code><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">http-equiv</span><span class="pun">=</span><span class="atv">"Cache-Control"</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"no-siteapp"</span><span class="pln"> </span><span class="tag">/&gt;</span></code></pre>
        <p>百度SiteApp转码声明：<a href="http://t.cn/R28wSBl" target="_blank">http://t.cn/R28wSBl</a></p>
        <p><strong>4. 设置状态栏的背景颜色（IOS）</strong></p>
        <p>设置状态栏的背景颜色，只有在<code>"apple-mobile-web-app-capable" content="yes"</code>时生效</p>
<pre class="prettyprint"><code><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"apple-mobile-web-app-status-bar-style"</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"black-translucent"</span><span class="pln"> </span><span class="tag">/&gt;</span><span class="pln"> </span></code></pre>
        <p>content 参数：</p>
        <ul>
            <li>default ：状态栏背景是白色。</li>
            <li>black ：状态栏背景是黑色。</li>
            <li>
                black-translucent ：状态栏背景是半透明。 如果设置为 default 或 black ,网页内容从状态栏底部开始。<br>
                如果设置为 black-translucent ,网页内容充满整个屏幕，顶部会被状态栏遮挡。
            </li>
        </ul>
        <p><strong>5.移动端手机号码识别（IOS）</strong></p>
        <p>在 iOS Safari （其他浏览器和Android均不会）上会对那些看起来像是电话号码的数字处理为电话链接，比如：</p>
        <ul>
            <li>7位数字，形如：1234567</li>
            <li>带括号及加号的数字，形如：(+86)123456789</li>
            <li>双连接线的数字，形如：00-00-00111</li>
            <li>11位数字，形如：13800138000</li>
        </ul>
        <p><strong>可能还有其他类型的数字也会被识别。我们可以通过如下的meta来关闭电话号码的自动识别：</strong></p>
<pre class="prettyprint"><code><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"format-detection"</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"telephone=no"</span><span class="pln"> </span><span class="tag">/&gt;</span></code></pre>
        <p><strong>开启电话功能</strong></p>
<pre class="prettyprint"><code><span class="tag">&lt;a</span><span class="pln"> </span><span class="atn">href</span><span class="pun">=</span><span class="atv">"tel:123456"</span><span class="tag">&gt;</span><span class="pln">123456</span><span class="tag">&lt;/a&gt;</span></code></pre>
        <p><strong>开启短信功能：</strong></p>
<pre class="prettyprint"><code><span class="tag">&lt;a</span><span class="pln"> </span><span class="atn">href</span><span class="pun">=</span><span class="atv">"sms:123456"</span><span class="tag">&gt;</span><span class="pln">123456</span><span class="tag">&lt;/a&gt;</span><span class="pln"> </span></code></pre>
        <p><strong>6. 移动端邮箱识别（Android）</strong></p>
        <p>与电话号码的识别一样，在安卓上会对符合邮箱格式的字符串进行识别，我们可以通过如下的meta来管别邮箱的自动识别：</p>
<pre class="prettyprint"><code><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"email=no"</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"format-detection"</span><span class="pln"> </span><span class="tag">/&gt;</span><span class="pln"> </span></code></pre>
        <p>同样地，我们也可以通过标签属性来开启长按邮箱地址弹出邮件发送的功能：</p>
<pre class="prettyprint"><code><span class="tag">&lt;a</span><span class="pln"> </span><span class="atn">mailto:dooyoe</span><span class="pln">@</span><span class="atn">gmail</span><span class="pln">.</span><span class="atn">com</span><span class="atv">"&gt;</span><span class="pln">dooyoe@gmail.com</span><span class="tag">&lt;/a&gt;</span><span class="pln"> </span></code></pre>
        <p><strong>7. 添加智能 App 广告条 Smart App Banner（IOS 6+ Safari）</strong></p>
<pre class="prettyprint"><code><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"apple-itunes-app"</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"app-id=myAppStoreID, affiliate-data=myAffiliateData, app-argument=myURL"</span><span class="tag">&gt;</span></code></pre>
        <p><strong>8. IOS Web app启动动画</strong></p>
        <p>由于iPad 的启动画面是不包括状态栏区域的。所以启动图片需要减去状态栏区域所对应的方向上的20px大小，相应地在retina设备上要减去40px的大小。</p>
<pre class="prettyprint"><code><span class="tag">&lt;link</span><span class="pln"> </span><span class="atn">href</span><span class="pun">=</span><span class="atv">"apple-touch-startup-image-320x460.png"</span><span class="pln"> </span><span class="atn">media</span><span class="pun">=</span><span class="atv">"(device-width: 320px)"</span><span class="pln"> </span><span class="atn">rel</span><span class="pun">=</span><span class="atv">"apple-touch-startup-image"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;link</span><span class="pln"> </span><span class="atn">href</span><span class="pun">=</span><span class="atv">"apple-touch-startup-image-640x960.png"</span><span class="pln"> </span><span class="atn">media</span><span class="pun">=</span><span class="atv">"(device-width: 320px) and (-webkit-device-pixel-ratio: 2)"</span><span class="pln"> </span><span class="atn">rel</span><span class="pun">=</span><span class="atv">"apple-touch-startup-image"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;link</span><span class="pln"> </span><span class="atn">href</span><span class="pun">=</span><span class="atv">"apple-touch-startup-image-768x1004.png"</span><span class="pln"> </span><span class="atn">media</span><span class="pun">=</span><span class="atv">"(device-width: 768px) and (orientation: portrait)"</span><span class="pln"> </span><span class="atn">rel</span><span class="pun">=</span><span class="atv">"apple-touch-startup-image"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;link</span><span class="pln"> </span><span class="atn">href</span><span class="pun">=</span><span class="atv">"apple-touch-startup-image-748x1024.png"</span><span class="pln"> </span><span class="atn">media</span><span class="pun">=</span><span class="atv">"(device-width: 768px) and (orientation: landscape)"</span><span class="pln"> </span><span class="atn">rel</span><span class="pun">=</span><span class="atv">"apple-touch-startup-image"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;link</span><span class="pln"> </span><span class="atn">href</span><span class="pun">=</span><span class="atv">"apple-touch-startup-image-1536x2008.png"</span><span class="pln"> </span><span class="atn">media</span><span class="pun">=</span><span class="atv">"(device-width: 1536px) and (orientation: portrait) and (-webkit-device-pixel-ratio: 2)"</span><span class="pln"> </span><span class="atn">rel</span><span class="pun">=</span><span class="atv">"apple-touch-startup-image"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;link</span><span class="pln"> </span><span class="atn">href</span><span class="pun">=</span><span class="atv">"apple-touch-startup-image-2048x1496.png"</span><span class="pln"> </span><span class="atn">media</span><span class="pun">=</span><span class="atv">"(device-width: 1536px)  and (orientation: landscape) and (-webkit-device-pixel-ratio: 2)"</span><span class="pln"> </span><span class="atn">rel</span><span class="pun">=</span><span class="atv">"apple-touch-startup-image"</span><span class="tag">&gt;</span></code></pre>
        <p>（<code>landscape：横屏</code> | <code>portrait：竖屏</code>）</p>
        <p><strong>9. 添加到主屏后的APP图标</strong></p>
        <p>指定web app添加到主屏后的图标路径，有两种略微不同的方式：</p>
<pre class="prettyprint"><code><span class="com">&lt;!-- 设计原图 --&gt;</span><span class="pln">
</span><span class="tag">&lt;link</span><span class="pln"> </span><span class="atn">href</span><span class="pun">=</span><span class="atv">"short_cut_114x114.png"</span><span class="pln"> </span><span class="atn">rel</span><span class="pun">=</span><span class="atv">"apple-touch-icon-precomposed"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="com">&lt;!-- 添加高光效果 --&gt;</span><span class="pln">
</span><span class="tag">&lt;link</span><span class="pln"> </span><span class="atn">href</span><span class="pun">=</span><span class="atv">"short_cut_114x114.png"</span><span class="pln"> </span><span class="atn">rel</span><span class="pun">=</span><span class="atv">"apple-touch-icon"</span><span class="tag">&gt;</span></code></pre>
        <ul>
            <li>apple-touch-icon：在IOS6及以下的版本会自动为图标添加一层高光效果（IOS7开始已使用扁平化的设计风格）</li>
            <li>apple-touch-icon-precomposed：使用“设计原图图标”</li>
        </ul>
        <p><strong>效果：</strong></p>
        <p><img src="http://img.mukewang.com/557fe3e600014a4d02380138.png" alt="图片描述"></p>
        <p><strong>图标尺寸：</strong></p>
        <p>可通过指定size属性来为不同的设备提供不同的图标（但通常来说，我们只需提供一个114 x 114 pixels大小的图标即可 ）</p>
        <p><strong>官方说明如下：</strong></p>
<pre class="prettyprint"><code><span class="typ">Create</span><span class="pln"> different sizes of your app icon </span><span class="kwd">for</span><span class="pln"> different devices</span><span class="pun">.</span><span class="pln"> </span><span class="typ">If</span><span class="pln"> you</span><span class="pun">’</span><span class="pln">re creating a universal app</span><span class="pun">,</span><span class="pln"> you need to supply app 
icons </span><span class="kwd">in</span><span class="pln"> all four sizes</span><span class="pun">.</span><span class="pln">
</span><span class="typ">For</span><span class="pln"> iPhone </span><span class="kwd">and</span><span class="pln"> iPod touch both of these sizes are required</span><span class="pun">:</span><span class="pln">
</span><span class="lit">57</span><span class="pln"> x </span><span class="lit">57</span><span class="pln"> pixels
</span><span class="lit">114</span><span class="pln"> x </span><span class="lit">114</span><span class="pln"> pixels </span><span class="pun">(</span><span class="pln">high resolution</span><span class="pun">)</span><span class="pln">
</span><span class="typ">For</span><span class="pln"> iPad</span><span class="pun">,</span><span class="pln"> both of these sizes are required</span><span class="pun">:</span><span class="pln">
</span><span class="lit">72</span><span class="pln"> x </span><span class="lit">72</span><span class="pln"> pixels
</span><span class="lit">144</span><span class="pln"> x </span><span class="lit">144</span><span class="pln"> </span><span class="pun">(</span><span class="pln">high resolution</span><span class="pun">)</span></code></pre>
        <p><strong>10. 优先使用最新版本 IE 和 Chrome</strong></p>
<pre class="prettyprint"><code><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">http-equiv</span><span class="pun">=</span><span class="atv">"X-UA-Compatible"</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"IE=edge,chrome=1"</span><span class="pln"> </span><span class="tag">/&gt;</span><span class="pln"> </span></code></pre>
        <p><strong>11.viewport模板</strong></p>
<pre class="prettyprint"><code><span class="tag">&lt;html&gt;</span><span class="pln">
</span><span class="tag">&lt;head&gt;</span><span class="pln">
</span><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">charset</span><span class="pun">=</span><span class="atv">"utf-8"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no"</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"viewport"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"yes"</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"apple-mobile-web-app-capable"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"black"</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"apple-mobile-web-app-status-bar-style"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"telephone=no"</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"format-detection"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"email=no"</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"format-detection"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;title&gt;</span><span class="pln">标题</span><span class="tag">&lt;/title&gt;</span><span class="pln">
</span><span class="tag">&lt;link</span><span class="pln"> </span><span class="atn">rel</span><span class="pun">=</span><span class="atv">"stylesheet"</span><span class="pln"> </span><span class="atn">href</span><span class="pun">=</span><span class="atv">"index.css"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;/head&gt;</span><span class="pln">
</span><span class="tag">&lt;body&gt;</span><span class="pln">
这里开始内容
</span><span class="tag">&lt;/body&gt;</span><span class="pln">
</span><span class="tag">&lt;/html&gt;</span></code></pre>
        <strong style="display:block;font-size:22px;margin:22px 0 10px"><strong>常见问题</strong></strong>
        <p><strong>1、移动端如何定义字体font-family</strong></p>
        <p>三大手机系统的字体：</p>
        <p><strong>iOS 系统</strong></p>
        <ul>
            <li>默认中文字体是Heiti SC</li>
            <li>默认英文字体是Helvetica</li>
            <li>默认数字字体是HelveticaNeue</li>
            <li>无微软雅黑字体</li>
        </ul>
        <p><strong>Android 系统</strong></p>
        <ul>
            <li>
                <p>默认中文字体是Droidsansfallback</p>
            </li>
            <li>
                <p>默认英文和数字字体是Droid Sans</p>
            </li>
            <li>无微软雅黑字体</li>
        </ul>
        <p><strong>Winphone 系统</strong></p>
        <ul>
            <li>
                <p>默认中文字体是Dengxian(方正等线体)</p>
            </li>
            <li>
                <p>默认英文和数字字体是Segoe</p>
            </li>
            <li>无微软雅黑字体</li>
        </ul>
        <p>各个手机系统有自己的默认字体，且都不支持微软雅黑，如无特殊需求，手机端无需定义中文字体，使用系统默认英文字体和数字字体可使用 Helvetica ，三种系统都支持。</p>
<pre class="prettyprint"><code><span class="pun">*</span><span class="pln"> </span><span class="pun">移动端定义字体的代码</span><span class="pln"> </span><span class="pun">*/</span><span class="pln">
body</span><span class="pun">{</span><span class="pln">font</span><span class="pun">-</span><span class="pln">family</span><span class="pun">:</span><span class="typ">Helvetica</span><span class="pun">;}</span></code></pre>
        <p><strong>2、移动端字体单位<code>font-size</code>选择<code>px</code>还是<code>rem</code></strong></p>
        <ul>
            <li>对于只需要适配手机设备，使用<code>px</code>即可</li>
            <li>对于需要适配各种移动设备，使用<code>rem</code>，例如只需要适配iPhone和iPad等分辨率差别比较挺大的设备</li>
        </ul>
        <p><code>rem</code>配置参考：</p>
<pre class="prettyprint"><code><span class="pln">html </span><span class="pun">{</span><span class="pln">font</span><span class="pun">-</span><span class="pln">size</span><span class="pun">:</span><span class="lit">10px</span><span class="pun">}</span><span class="pln">
</span><span class="lit">@media</span><span class="pln"> screen </span><span class="kwd">and</span><span class="pln"> </span><span class="pun">(</span><span class="pln">min</span><span class="pun">-</span><span class="pln">width</span><span class="pun">:</span><span class="lit">480px</span><span class="pun">)</span><span class="pln"> </span><span class="kwd">and</span><span class="pln"> </span><span class="pun">(</span><span class="pln">max</span><span class="pun">-</span><span class="pln">width</span><span class="pun">:</span><span class="lit">639px</span><span class="pun">)</span><span class="pln"> </span><span class="pun">{</span><span class="pln">
    html </span><span class="pun">{</span><span class="pln">
        font</span><span class="pun">-</span><span class="pln">size</span><span class="pun">:</span><span class="pln"> </span><span class="lit">15px</span><span class="pln">
    </span><span class="pun">}</span><span class="pln">
</span><span class="pun">}</span><span class="pln">
</span><span class="lit">@media</span><span class="pln"> screen </span><span class="kwd">and</span><span class="pln"> </span><span class="pun">(</span><span class="pln">min</span><span class="pun">-</span><span class="pln">width</span><span class="pun">:</span><span class="lit">640px</span><span class="pun">)</span><span class="pln"> </span><span class="kwd">and</span><span class="pln"> </span><span class="pun">(</span><span class="pln">max</span><span class="pun">-</span><span class="pln">width</span><span class="pun">:</span><span class="lit">719px</span><span class="pun">)</span><span class="pln"> </span><span class="pun">{</span><span class="pln">
    html </span><span class="pun">{</span><span class="pln">
        font</span><span class="pun">-</span><span class="pln">size</span><span class="pun">:</span><span class="pln"> </span><span class="lit">20px</span><span class="pln">
    </span><span class="pun">}</span><span class="pln">
</span><span class="pun">}</span><span class="pln">
</span><span class="lit">@media</span><span class="pln"> screen </span><span class="kwd">and</span><span class="pln"> </span><span class="pun">(</span><span class="pln">min</span><span class="pun">-</span><span class="pln">width</span><span class="pun">:</span><span class="lit">720px</span><span class="pun">)</span><span class="pln"> </span><span class="kwd">and</span><span class="pln"> </span><span class="pun">(</span><span class="pln">max</span><span class="pun">-</span><span class="pln">width</span><span class="pun">:</span><span class="lit">749px</span><span class="pun">)</span><span class="pln"> </span><span class="pun">{</span><span class="pln">
    html </span><span class="pun">{</span><span class="pln">
        font</span><span class="pun">-</span><span class="pln">size</span><span class="pun">:</span><span class="pln"> </span><span class="lit">22.5px</span><span class="pln">
    </span><span class="pun">}</span><span class="pln">
</span><span class="pun">}</span><span class="pln">
</span><span class="lit">@media</span><span class="pln"> screen </span><span class="kwd">and</span><span class="pln"> </span><span class="pun">(</span><span class="pln">min</span><span class="pun">-</span><span class="pln">width</span><span class="pun">:</span><span class="lit">750px</span><span class="pun">)</span><span class="pln"> </span><span class="kwd">and</span><span class="pln"> </span><span class="pun">(</span><span class="pln">max</span><span class="pun">-</span><span class="pln">width</span><span class="pun">:</span><span class="lit">799px</span><span class="pun">)</span><span class="pln"> </span><span class="pun">{</span><span class="pln">
    html </span><span class="pun">{</span><span class="pln">
        font</span><span class="pun">-</span><span class="pln">size</span><span class="pun">:</span><span class="pln"> </span><span class="lit">23.5px</span><span class="pln">
    </span><span class="pun">}</span><span class="pln">
</span><span class="pun">}</span><span class="pln">
</span><span class="lit">@media</span><span class="pln"> screen </span><span class="kwd">and</span><span class="pln"> </span><span class="pun">(</span><span class="pln">min</span><span class="pun">-</span><span class="pln">width</span><span class="pun">:</span><span class="lit">800px</span><span class="pun">)</span><span class="pln"> </span><span class="kwd">and</span><span class="pln"> </span><span class="pun">(</span><span class="pln">max</span><span class="pun">-</span><span class="pln">width</span><span class="pun">:</span><span class="lit">959px</span><span class="pun">)</span><span class="pln"> </span><span class="pun">{</span><span class="pln">
    html </span><span class="pun">{</span><span class="pln">
        font</span><span class="pun">-</span><span class="pln">size</span><span class="pun">:</span><span class="pln"> </span><span class="lit">25px</span><span class="pln">
    </span><span class="pun">}</span><span class="pln">
</span><span class="pun">}</span><span class="pln">
</span><span class="lit">@media</span><span class="pln"> screen </span><span class="kwd">and</span><span class="pln"> </span><span class="pun">(</span><span class="pln">min</span><span class="pun">-</span><span class="pln">width</span><span class="pun">:</span><span class="lit">960px</span><span class="pun">)</span><span class="pln"> </span><span class="kwd">and</span><span class="pln"> </span><span class="pun">(</span><span class="pln">max</span><span class="pun">-</span><span class="pln">width</span><span class="pun">:</span><span class="lit">1079px</span><span class="pun">)</span><span class="pln"> </span><span class="pun">{</span><span class="pln">
    html </span><span class="pun">{</span><span class="pln">
        font</span><span class="pun">-</span><span class="pln">size</span><span class="pun">:</span><span class="pln"> </span><span class="lit">30px</span><span class="pln">
    </span><span class="pun">}</span><span class="pln">
</span><span class="pun">}</span><span class="pln">
</span><span class="lit">@media</span><span class="pln"> screen </span><span class="kwd">and</span><span class="pln"> </span><span class="pun">(</span><span class="pln">min</span><span class="pun">-</span><span class="pln">width</span><span class="pun">:</span><span class="lit">1080px</span><span class="pun">)</span><span class="pln"> </span><span class="pun">{</span><span class="pln">
    html </span><span class="pun">{</span><span class="pln">
        font</span><span class="pun">-</span><span class="pln">size</span><span class="pun">:</span><span class="pln"> </span><span class="lit">32px</span><span class="pln">
    </span><span class="pun">}</span><span class="pln">
</span><span class="pun">}</span></code></pre>
        <p><strong>3、移动端touch事件(区分webkit 和 winphone)</strong></p>
        <p>当用户手指放在移动设备在屏幕上滑动会触发的touch事件</p>
        <p><strong>以下支持webkit</strong></p>
        <ul>
            <li>touchstart——当手指触碰屏幕时候发生。不管当前有多少只手指</li>
            <li>touchmove——当手指在屏幕上滑动时连续触发。通常我们再滑屏页面，会调用event的preventDefault()可以阻止默认情况的发生：阻止页面滚动</li>
            <li>touchend——当手指离开屏幕时触发</li>
            <li>touchcancel——系统停止跟踪触摸时候会触发。例如在触摸过程中突然页面alert()一个提示框，此时会触发该事件，这个事件比较少用</li>
        </ul>
        <p><strong>以下支持winphone 8</strong></p>
        <ul>
            <li>MSPointerDown——当手指触碰屏幕时候发生。不管当前有多少只手指</li>
            <li>
                MSPointerMove——当手指在屏幕上滑动时连续触发。通常我们再滑屏页面，会调用css的html{-ms-touch-action:<br>
                none;}可以阻止默认情况的发生：阻止页面滚动
            </li>
            <li>MSPointerUp——当手指离开屏幕时触发</li>
        </ul>
        <p><strong>4、移动端click屏幕产生200-300 ms的延迟响应</strong></p>
        <p>移动设备上的web网页是有300ms延迟的，玩玩会造成按钮点击延迟甚至是点击失效。</p>
        <p>以下是历史原因：</p>
        <p>2007年苹果发布首款iphone上IOS系统搭载的safari为了将适用于PC端上大屏幕的网页能比较好的展示在手机端上，使用了双击缩放(double tap to zoom)的方案，比如你在手机上用浏览器打开一个PC上的网页，你可能在看到页面内容虽然可以撑满整个屏幕，但是字体、图片都很小看不清，此时可以快速双击屏幕上的某一部分，你就能看清该部分放大后的内容，再次双击后能回到原始状态。</p>
        <p>双击缩放是指用手指在屏幕上快速点击两次，iOS 自带的 Safari 浏览器会将网页缩放至原始比例。</p>
        <p>原因就出在浏览器需要如何判断快速点击上，当用户在屏幕上单击某一个元素时候，例如跳转链接，此处浏览器会先捕获该次单击，但浏览器不能决定用户是单纯要点击链接还是要双击该部分区域进行缩放操作，所以，捕获第一次单击后，浏览器会先Hold一段时间t，如果在t时间区间里用户未进行下一次点击，则浏览器会做单击跳转链接的处理，如果t时间里用户进行了第二次单击操作，则浏览器会禁止跳转，转而进行对该部分区域页面的缩放操作。那么这个时间区间t有多少呢？在IOS safari下，大概为300毫秒。这就是延迟的由来。造成的后果用户纯粹单击页面，页面需要过一段时间才响应，给用户慢体验感觉，对于web开发者来说是，页面js捕获click事件的回调函数处理，需要300ms后才生效，也就间接导致影响其他业务逻辑的处理。</p>
        <p><strong>解决方案：</strong></p>
        <ul>
            <li>fastclick可以解决在手机上点击事件的300ms延迟</li>
            <li>zepto的touch模块，tap事件也是为了解决在click的延迟问题</li>
        </ul>
        <p><strong>触摸事件的响应顺序</strong></p>
<pre class="prettyprint"><code><span class="lit">1</span><span class="pun">、</span><span class="pln">ontouchstart
</span><span class="lit">2</span><span class="pun">、</span><span class="pln">ontouchmove
</span><span class="lit">3</span><span class="pun">、</span><span class="pln">ontouchend
</span><span class="lit">4</span><span class="pun">、</span><span class="pln">onclick</span></code></pre>
        <p>解决300ms延迟的问题，也可以通过绑定ontouchstart事件，加快对事件的响应。</p>
        <p><strong>5、什么是Retina 显示屏，带来了什么问题</strong></p>
        <p><code>retina</code>：一种具备超高像素密度的液晶屏，同样大小的屏幕上显示的像素点由1个变为多个，如在同样带下的屏幕上，苹果设备的retina显示屏中，像素点1个变为4个</p>
        <p>在高清显示屏中的位图被放大，图片会变得模糊，<strong>因此移动端的视觉稿通常会设计为传统PC的2倍</strong>。</p>
        <p>那么，前端的应对方案是：</p>
        <p>设计稿切出来的图片长宽保证为偶数，并使用<code>backgroud-size</code>把图片缩小为原来的1/2</p>
<pre class="prettyprint"><code><span class="com">//例如图片宽高为：200px*200px，那么写法如下</span><span class="pln">
</span><span class="pun">.</span><span class="pln">css</span><span class="pun">{</span><span class="pln">width</span><span class="pun">:</span><span class="lit">100px</span><span class="pun">;</span><span class="pln">height</span><span class="pun">:</span><span class="lit">100px</span><span class="pun">;</span><span class="pln">background</span><span class="pun">-</span><span class="pln">size</span><span class="pun">:</span><span class="lit">100px</span><span class="pln"> </span><span class="lit">100px</span><span class="pun">;}</span></code></pre>
        <p>其它元素的取值为原来的1/2，例如视觉稿40px的字体，使用样式的写法为20px</p>
<pre class="prettyprint"><code><span class="pun">.</span><span class="pln">css</span><span class="pun">{</span><span class="pln">font</span><span class="pun">-</span><span class="pln">size</span><span class="pun">:</span><span class="lit">20px</span><span class="pun">}</span></code></pre>
        <p><strong>6、ios系统中元素被触摸时产生的半透明灰色遮罩怎么去掉</strong></p>
        <p>ios用户点击一个链接，会出现一个半透明灰色遮罩, 如果想要禁用，可设置-webkit-tap-highlight-color的alpha值为0，也就是属性值的最后一位设置为0就可以去除半透明灰色遮罩。</p>
<pre class="prettyprint"><code><span class="pln">a</span><span class="pun">,</span><span class="pln">button</span><span class="pun">,</span><span class="pln">input</span><span class="pun">,</span><span class="pln">textarea</span><span class="pun">{-</span><span class="pln">webkit</span><span class="pun">-</span><span class="pln">tap</span><span class="pun">-</span><span class="pln">highlight</span><span class="pun">-</span><span class="pln">color</span><span class="pun">:</span><span class="pln"> rgba</span><span class="pun">(</span><span class="lit">0</span><span class="pun">,</span><span class="lit">0</span><span class="pun">,</span><span class="lit">0</span><span class="pun">,</span><span class="lit">0</span><span class="pun">;)}</span></code></pre>
        <p><strong>7、部分android系统中元素被点击时产生的边框怎么去掉</strong></p>
        <p>android用户点击一个链接，会出现一个边框或者半透明灰色遮罩, 不同生产商定义出来额效果不一样，可设置<code>-webkit-tap-highlight-color</code>的<code>alpha值</code>为0去除部分机器自带的效果。</p>
<pre class="prettyprint"><code><span class="pln">a</span><span class="pun">,</span><span class="pln">button</span><span class="pun">,</span><span class="pln">input</span><span class="pun">,</span><span class="pln">textarea</span><span class="pun">{</span><span class="pln">
    </span><span class="pun">-</span><span class="pln">webkit</span><span class="pun">-</span><span class="pln">tap</span><span class="pun">-</span><span class="pln">highlight</span><span class="pun">-</span><span class="pln">color</span><span class="pun">:</span><span class="pln"> rgba</span><span class="pun">(</span><span class="lit">0</span><span class="pun">,</span><span class="lit">0</span><span class="pun">,</span><span class="lit">0</span><span class="pun">,</span><span class="lit">0</span><span class="pun">;)</span><span class="pln">
    </span><span class="pun">-</span><span class="pln">webkit</span><span class="pun">-</span><span class="pln">user</span><span class="pun">-</span><span class="pln">modify</span><span class="pun">:</span><span class="pln">read</span><span class="pun">-</span><span class="pln">write</span><span class="pun">-</span><span class="pln">plaintext</span><span class="pun">-</span><span class="pln">only</span><span class="pun">;</span><span class="pln"> 
</span><span class="pun">}</span></code></pre>
        <p><code>-webkit-user-modify</code>有个副作用，就是输入法不再能够输入多个字符。</p>
        <p>另外，有些机型去除不了，如小米2</p>
        <p>对于按钮类还有个办法，不使用a或者input标签，直接用div标签</p>
        <p><strong>8、winphone系统a、input标签被点击时产生的半透明灰色背景怎么去掉</strong></p>
<pre class="prettyprint"><code><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"msapplication-tap-highlight"</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"no"</span><span class="tag">&gt;</span></code></pre>
        <p><strong>9、webkit表单元素的默认外观怎么重置</strong></p>
<pre class="prettyprint"><code><span class="pun">.</span><span class="pln">css</span><span class="pun">{-</span><span class="pln">webkit</span><span class="pun">-</span><span class="pln">appearance</span><span class="pun">:</span><span class="pln">none</span><span class="pun">;}</span></code></pre>
        <p><strong>10、webkit表单输入框placeholder的颜色值能改变么</strong></p>
<pre class="prettyprint"><code><span class="pln">input</span><span class="pun">::-</span><span class="pln">webkit</span><span class="pun">-</span><span class="pln">input</span><span class="pun">-</span><span class="pln">placeholder</span><span class="pun">{</span><span class="pln">color</span><span class="pun">:</span><span class="com">#AAAAAA;}</span><span class="pln">
input</span><span class="pun">:</span><span class="pln">focus</span><span class="pun">::-</span><span class="pln">webkit</span><span class="pun">-</span><span class="pln">input</span><span class="pun">-</span><span class="pln">placeholder</span><span class="pun">{</span><span class="pln">color</span><span class="pun">:</span><span class="com">#E</span></code></pre>
        <p><strong>11、webkit表单输入框placeholder的文字能换行么</strong></p>
        <p>iOS可以，Android不行~</p>
        <ol>
            <li>关闭iOS键盘首字母自动大写</li>
        </ol>
        <p>在iOS中，默认情况下键盘是开启首字母大写的功能的，如果启用这个功能，可以这样：</p>
<pre class="prettyprint"><code><span class="tag">&lt;input</span><span class="pln"> </span><span class="atn">type</span><span class="pun">=</span><span class="atv">"text"</span><span class="pln"> </span><span class="atn">autocapitalize</span><span class="pun">=</span><span class="atv">"off"</span><span class="pln"> </span><span class="tag">/&gt;</span></code></pre>
        <p><strong>13. 关闭iOS输入自动修正</strong></p>
        <p>和英文输入默认自动首字母大写那样，IOS还做了一个功能，默认输入法会开启自动修正输入内容，这样的话，用户经常要操作两次。如果不希望开启此功能，我们可以通过input标签属性来关闭掉：</p>
<pre class="prettyprint"><code><span class="tag">&lt;input</span><span class="pln"> </span><span class="atn">type</span><span class="pun">=</span><span class="atv">"text"</span><span class="pln"> </span><span class="atn">autocorrect</span><span class="pun">=</span><span class="atv">"off"</span><span class="pln"> </span><span class="tag">/&gt;</span><span class="pln"> </span></code></pre>
        <p><strong>14. 禁止文本缩放</strong></p>
        <p>当移动设备横竖屏切换时，文本的大小会重新计算，进行相应的缩放，当我们不需要这种情况时，可以选择禁止：</p>
<pre class="prettyprint"><code><span class="pln">html </span><span class="pun">{</span><span class="pln">
　　        </span><span class="pun">-</span><span class="pln">webkit</span><span class="pun">-</span><span class="pln">text</span><span class="pun">-</span><span class="pln">size</span><span class="pun">-</span><span class="pln">adjust</span><span class="pun">:</span><span class="pln"> </span><span class="lit">100</span><span class="pun">%;</span><span class="pln">
</span><span class="pun">}</span></code></pre>
        <p>需要注意的是，PC端的该属性已经被移除，该属性在移动端要生效，必须设置 <code>meta viewport</code>。</p>
        <p><strong>15. 移动端如何清除输入框内阴影</strong></p>
        <p>在iOS上，输入框默认有内部阴影，但无法使用 <code>box-shadow</code> 来清除，如果不需要阴影，可以这样关闭：</p>
<pre class="prettyprint"><code><span class="pln">input</span><span class="pun">,</span><span class="pln">
textarea </span><span class="pun">{</span><span class="pln">
　　border</span><span class="pun">:</span><span class="pln"> </span><span class="lit">0</span><span class="pun">;</span><span class="pln"> </span><span class="com">/* 方法1 */</span><span class="pln">
　　</span><span class="pun">-</span><span class="pln">webkit</span><span class="pun">-</span><span class="pln">appearance</span><span class="pun">:</span><span class="pln"> none</span><span class="pun">;</span><span class="pln"> </span><span class="com">/* 方法2 */</span><span class="pln">
</span><span class="pun">}</span></code></pre>
        <p><strong>16. 快速回弹滚动</strong></p>
        <p>我们先来看看回弹滚动在手机浏览器发展的历史：</p>
        <ul>
            <li>早期的时候，移动端的浏览器都不支持非body元素的滚动条，所以一般都借助 iScroll;</li>
            <li>Android 3.0/iOS解决了非body元素的滚动问题，但滚动条不可见，同时iOS上只能通过2个手指进行滚动；</li>
            <li>Android 4.0解决了滚动条不可见及增加了快速回弹滚动效果，不过随后这个特性又被移除；</li>
            <li>iOS从5.0开始解决了滚动条不可见及增加了快速回弹滚动效果</li>
        </ul>
        <p>在iOS上如果你想让一个元素拥有像 Native 的滚动效果，你可以这样做：</p>
<pre class="prettyprint"><code><span class="pln"> </span><span class="pun">.</span><span class="pln">xxx </span><span class="pun">{</span><span class="pln">
        overflow</span><span class="pun">:</span><span class="pln"> </span><span class="kwd">auto</span><span class="pun">;</span><span class="pln"> </span><span class="com">/* auto | scroll */</span><span class="pln">
        </span><span class="pun">-</span><span class="pln">webkit</span><span class="pun">-</span><span class="pln">overflow</span><span class="pun">-</span><span class="pln">scrolling</span><span class="pun">:</span><span class="pln"> touch</span><span class="pun">;</span><span class="pln">
    </span><span class="pun">}</span></code></pre>
        <p>PS：iScroll用过之后感觉不是很好，有一些诡异的bug，这里推荐另外一个 iDangero Swiper，这个插件集成了滑屏滚动的强大功能（支持3D），而且还有回弹滚动的内置滚动条。<strong>iDangero官方地址：</strong> :www.idangero.us/swiper/#.VX_t9PmEB8Y</p>
        <p><strong>17. 移动端禁止选中内容</strong></p>
        <p>如果你不想用户可以选中页面中的内容，那么你可以在css中禁掉：</p>
<pre class="prettyprint"><code><span class="pun">.</span><span class="pln">user</span><span class="pun">-</span><span class="kwd">select</span><span class="pun">-</span><span class="pln">none </span><span class="pun">{</span><span class="pln">
  </span><span class="pun">-</span><span class="pln">webkit</span><span class="pun">-</span><span class="pln">user</span><span class="pun">-</span><span class="kwd">select</span><span class="pun">:</span><span class="pln"> none</span><span class="pun">;</span><span class="pln">  </span><span class="com">/* Chrome all / Safari all */</span><span class="pln">
  </span><span class="pun">-</span><span class="pln">moz</span><span class="pun">-</span><span class="pln">user</span><span class="pun">-</span><span class="kwd">select</span><span class="pun">:</span><span class="pln"> none</span><span class="pun">;</span><span class="pln">     </span><span class="com">/* Firefox all （移动端不需要） */</span><span class="pln">
  </span><span class="pun">-</span><span class="pln">ms</span><span class="pun">-</span><span class="pln">user</span><span class="pun">-</span><span class="kwd">select</span><span class="pun">:</span><span class="pln"> none</span><span class="pun">;</span><span class="pln">      </span><span class="com">/* IE 10+ */</span><span class="pln">      
</span><span class="pun">}</span></code></pre>
        <p><strong>18. 移动端取消touch高亮效果</strong></p>
        <p>在做移动端页面时，会发现所有a标签在触发点击时或者所有设置了<code>伪类 :active</code> 的元素，默认都会在激活状态时，显示高亮框，如果不想要这个高亮，那么你可以通过css以下方法来进行全局的禁止：</p>
<pre class="prettyprint"><code><span class="pln">html </span><span class="pun">{</span><span class="pln">
    </span><span class="pun">-</span><span class="pln">webkit</span><span class="pun">-</span><span class="pln">tap</span><span class="pun">-</span><span class="pln">highlight</span><span class="pun">-</span><span class="pln">color</span><span class="pun">:</span><span class="pln"> rgba</span><span class="pun">(</span><span class="lit">0</span><span class="pun">,</span><span class="pln"> </span><span class="lit">0</span><span class="pun">,</span><span class="pln"> </span><span class="lit">0</span><span class="pun">,</span><span class="pln"> </span><span class="lit">0</span><span class="pun">);</span><span class="pln">
</span><span class="pun">}</span></code></pre>
        <p>但这个方法在三星的机子上无效，有一种妥协的方法是把页面非真实跳转链接的<code>a标签</code>换成其它标签，可以解决这个问题。</p>
        <p><strong>19. 如何禁止保存或拷贝图像（IOS）</strong></p>
        <p>通常当你在手机或者pad上长按图像 img ，会弹出选项存储图像 或者拷贝图像，如果你不想让用户这么操作，那么你可以通过以下方法来禁止：</p>
<pre class="prettyprint"><code><span class="pln">img </span><span class="pun">{</span><span class="pln"> </span><span class="pun">-</span><span class="pln">webkit</span><span class="pun">-</span><span class="pln">touch</span><span class="pun">-</span><span class="pln">callout</span><span class="pun">:</span><span class="pln"> none</span><span class="pun">;</span><span class="pln"> </span><span class="pun">}</span></code></pre>
        <p><strong>20.模拟按钮hover效果</strong></p>
        <p>移动端触摸按钮的效果，可明示用户有些事情正要发生，是一个比较好体验，但是移动设备中并没有鼠标指针，使用css的hover并不能满足我们的需求，还好国外有个激活css的active效果，代码如下，</p>
<pre class="prettyprint"><code><span class="tag">&lt;html&gt;</span><span class="pln">
</span><span class="tag">&lt;head&gt;</span><span class="pln">
</span><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">charset</span><span class="pun">=</span><span class="atv">"utf-8"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no"</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"viewport"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"yes"</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"apple-mobile-web-app-capable"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"black"</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"apple-mobile-web-app-status-bar-style"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"telephone=no"</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"format-detection"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"email=no"</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"format-detection"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;style</span><span class="pln"> </span><span class="atn">type</span><span class="pun">=</span><span class="atv">"text/css"</span><span class="tag">&gt;</span><span class="pln">
a</span><span class="pun">{-</span><span class="pln">webkit</span><span class="pun">-</span><span class="pln">tap</span><span class="pun">-</span><span class="pln">highlight</span><span class="pun">-</span><span class="pln">color</span><span class="pun">:</span><span class="pln"> rgba</span><span class="pun">(</span><span class="lit">0</span><span class="pun">,</span><span class="lit">0</span><span class="pun">,</span><span class="lit">0</span><span class="pun">,</span><span class="lit">0</span><span class="pun">);}</span><span class="pln">
</span><span class="pun">.</span><span class="pln">btn</span><span class="pun">-</span><span class="pln">blue</span><span class="pun">{</span><span class="pln">display</span><span class="pun">:</span><span class="pln">block</span><span class="pun">;</span><span class="pln">height</span><span class="pun">:</span><span class="lit">42px</span><span class="pun">;</span><span class="pln">line</span><span class="pun">-</span><span class="pln">height</span><span class="pun">:</span><span class="lit">42px</span><span class="pun">;</span><span class="pln">text</span><span class="pun">-</span><span class="pln">align</span><span class="pun">:</span><span class="pln">center</span><span class="pun">;</span><span class="pln">border</span><span class="pun">-</span><span class="pln">radius</span><span class="pun">:</span><span class="lit">4px</span><span class="pun">;</span><span class="pln">font</span><span class="pun">-</span><span class="pln">size</span><span class="pun">:</span><span class="lit">18px</span><span class="pun">;</span><span class="pln">color</span><span class="pun">:</span><span class="com">#FFFFFF;background-color: #4185F3;}</span><span class="pln">
</span><span class="pun">.</span><span class="pln">btn</span><span class="pun">-</span><span class="pln">blue</span><span class="pun">:</span><span class="pln">active</span><span class="pun">{</span><span class="pln">background</span><span class="pun">-</span><span class="pln">color</span><span class="pun">:</span><span class="pln"> </span><span class="com">#357AE8;}</span><span class="pln">
</span><span class="tag">&lt;/style&gt;</span><span class="pln">
</span><span class="tag">&lt;/head&gt;</span><span class="pln">
</span><span class="tag">&lt;body&gt;</span><span class="pln">
</span><span class="tag">&lt;div</span><span class="pln"> </span><span class="atn">class</span><span class="pun">=</span><span class="atv">"btn-blue"</span><span class="tag">&gt;</span><span class="pln">按钮</span><span class="tag">&lt;/div&gt;</span><span class="pln">
</span><span class="tag">&lt;script</span><span class="pln"> </span><span class="atn">type</span><span class="pun">=</span><span class="atv">"text/javascript"</span><span class="tag">&gt;</span><span class="pln">
document</span><span class="pun">.</span><span class="pln">addEventListener</span><span class="pun">(</span><span class="str">"touchstart"</span><span class="pun">,</span><span class="pln"> </span><span class="kwd">function</span><span class="pun">(){},</span><span class="pln"> </span><span class="kwd">true</span><span class="pun">)</span><span class="pln">
</span><span class="tag">&lt;/script&gt;</span><span class="pln">
</span><span class="tag">&lt;/body&gt;</span><span class="pln">
</span><span class="tag">&lt;/html&gt;</span></code></pre>
        <p>兼容性ios5+、部分android 4+、winphone 8</p>
        <p>要做到全兼容的办法，可通过绑定<code>ontouchstart</code>和<code>ontouchend</code>来控制按钮的类名。</p>
<pre class="prettyprint"><code><span class="tag">&lt;html&gt;</span><span class="pln">
</span><span class="tag">&lt;head&gt;</span><span class="pln">
</span><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">charset</span><span class="pun">=</span><span class="atv">"utf-8"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no"</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"viewport"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"yes"</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"apple-mobile-web-app-capable"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"black"</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"apple-mobile-web-app-status-bar-style"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"telephone=no"</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"format-detection"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;meta</span><span class="pln"> </span><span class="atn">content</span><span class="pun">=</span><span class="atv">"email=no"</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"format-detection"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="tag">&lt;style</span><span class="pln"> </span><span class="atn">type</span><span class="pun">=</span><span class="atv">"text/css"</span><span class="tag">&gt;</span><span class="pln">
a</span><span class="pun">{-</span><span class="pln">webkit</span><span class="pun">-</span><span class="pln">tap</span><span class="pun">-</span><span class="pln">highlight</span><span class="pun">-</span><span class="pln">color</span><span class="pun">:</span><span class="pln"> rgba</span><span class="pun">(</span><span class="lit">0</span><span class="pun">,</span><span class="lit">0</span><span class="pun">,</span><span class="lit">0</span><span class="pun">,</span><span class="lit">0</span><span class="pun">);}</span><span class="pln">
</span><span class="pun">.</span><span class="pln">btn</span><span class="pun">-</span><span class="pln">blue</span><span class="pun">{</span><span class="pln">display</span><span class="pun">:</span><span class="pln">block</span><span class="pun">;</span><span class="pln">height</span><span class="pun">:</span><span class="lit">42px</span><span class="pun">;</span><span class="pln">line</span><span class="pun">-</span><span class="pln">height</span><span class="pun">:</span><span class="lit">42px</span><span class="pun">;</span><span class="pln">text</span><span class="pun">-</span><span class="pln">align</span><span class="pun">:</span><span class="pln">center</span><span class="pun">;</span><span class="pln">border</span><span class="pun">-</span><span class="pln">radius</span><span class="pun">:</span><span class="lit">4px</span><span class="pun">;</span><span class="pln">font</span><span class="pun">-</span><span class="pln">size</span><span class="pun">:</span><span class="lit">18px</span><span class="pun">;</span><span class="pln">color</span><span class="pun">:</span><span class="com">#FFFFFF;background-color: #4185F3;}</span><span class="pln">
</span><span class="pun">.</span><span class="pln">btn</span><span class="pun">-</span><span class="pln">blue</span><span class="pun">-</span><span class="pln">on</span><span class="pun">{</span><span class="pln">background</span><span class="pun">-</span><span class="pln">color</span><span class="pun">:</span><span class="pln"> </span><span class="com">#357AE8;}</span><span class="pln">
</span><span class="tag">&lt;/style&gt;</span><span class="pln">
</span><span class="tag">&lt;/head&gt;</span><span class="pln">
</span><span class="tag">&lt;body&gt;</span><span class="pln">
</span><span class="tag">&lt;div</span><span class="pln"> </span><span class="atn">class</span><span class="pun">=</span><span class="atv">"btn-blue"</span><span class="tag">&gt;</span><span class="pln">按钮</span><span class="tag">&lt;/div&gt;</span><span class="pln">
</span><span class="tag">&lt;script</span><span class="pln"> </span><span class="atn">type</span><span class="pun">=</span><span class="atv">"text/javascript"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="kwd">var</span><span class="pln"> btnBlue </span><span class="pun">=</span><span class="pln"> document</span><span class="pun">.</span><span class="pln">querySelector</span><span class="pun">(</span><span class="str">".btn-blue"</span><span class="pun">);</span><span class="pln">
btnBlue</span><span class="pun">.</span><span class="pln">ontouchstart </span><span class="pun">=</span><span class="pln"> </span><span class="kwd">function</span><span class="pun">(){</span><span class="pln">
    </span><span class="kwd">this</span><span class="pun">.</span><span class="pln">className </span><span class="pun">=</span><span class="pln"> </span><span class="str">"btn-blue btn-blue-on"</span><span class="pln">
</span><span class="pun">}</span><span class="pln">
btnBlue</span><span class="pun">.</span><span class="pln">ontouchend </span><span class="pun">=</span><span class="pln"> </span><span class="kwd">function</span><span class="pun">(){</span><span class="pln">
    </span><span class="kwd">this</span><span class="pun">.</span><span class="pln">className </span><span class="pun">=</span><span class="pln"> </span><span class="str">"btn-blue"</span><span class="pln">
</span><span class="pun">}</span><span class="pln">
</span><span class="tag">&lt;/script&gt;</span><span class="pln">
</span><span class="tag">&lt;/body&gt;</span><span class="pln">
</span><span class="tag">&lt;/html&gt;</span></code></pre>
        <p><strong>21.屏幕旋转的事件和样式</strong></p>
        <p><strong>事件</strong></p>
        <p><code>window.orientation</code>，取值：正负90表示横屏模式、0和180表现为竖屏模式；</p>
<pre class="prettyprint"><code><span class="pln">window</span><span class="pun">.</span><span class="pln">onorientationchange </span><span class="pun">=</span><span class="pln"> </span><span class="kwd">function</span><span class="pun">(){</span><span class="pln">
            </span><span class="kwd">switch</span><span class="pun">(</span><span class="pln">window</span><span class="pun">.</span><span class="pln">orientation</span><span class="pun">){</span><span class="pln">
                </span><span class="kwd">case</span><span class="pln"> </span><span class="pun">-</span><span class="lit">90</span><span class="pun">:</span><span class="pln">
                </span><span class="kwd">case</span><span class="pln"> </span><span class="lit">90</span><span class="pun">:</span><span class="pln">
                alert</span><span class="pun">(</span><span class="str">"横屏:"</span><span class="pln"> </span><span class="pun">+</span><span class="pln"> window</span><span class="pun">.</span><span class="pln">orientation</span><span class="pun">);</span><span class="pln">
                </span><span class="kwd">case</span><span class="pln"> </span><span class="lit">0</span><span class="pun">:</span><span class="pln">
                </span><span class="kwd">case</span><span class="pln"> </span><span class="lit">180</span><span class="pun">:</span><span class="pln">
                alert</span><span class="pun">(</span><span class="str">"竖屏:"</span><span class="pln"> </span><span class="pun">+</span><span class="pln"> window</span><span class="pun">.</span><span class="pln">orientation</span><span class="pun">);</span><span class="pln">
                </span><span class="kwd">break</span><span class="pun">;</span><span class="pln">
            </span><span class="pun">}</span><span class="pln">
</span><span class="pun">}</span><span class="pln"> </span></code></pre>
        <p><strong>样式</strong></p>
<pre class="prettyprint"><code><span class="com">//竖屏时使用的样式</span><span class="pln">
</span><span class="lit">@media</span><span class="pln"> all </span><span class="kwd">and</span><span class="pln"> </span><span class="pun">(</span><span class="pln">orientation</span><span class="pun">:</span><span class="pln">portrait</span><span class="pun">)</span><span class="pln"> </span><span class="pun">{</span><span class="pln">
    </span><span class="pun">.</span><span class="pln">css</span><span class="pun">{}</span><span class="pln">
</span><span class="pun">}</span><span class="pln">
</span><span class="com">//横屏时使用的样式</span><span class="pln">
</span><span class="lit">@media</span><span class="pln"> all </span><span class="kwd">and</span><span class="pln"> </span><span class="pun">(</span><span class="pln">orientation</span><span class="pun">:</span><span class="pln">landscape</span><span class="pun">)</span><span class="pln"> </span><span class="pun">{</span><span class="pln">
    </span><span class="pun">.</span><span class="pln">css</span><span class="pun">{}</span><span class="pln">
</span><span class="pun">}</span></code></pre>
        <p><strong>22.audio元素和video元素在ios和andriod中无法自动播放</strong></p>
        <p>应对方案：触屏即播</p>
<pre class="prettyprint"><code><span class="pln">$</span><span class="pun">(</span><span class="str">'html'</span><span class="pun">).</span><span class="pln">one</span><span class="pun">(</span><span class="str">'touchstart'</span><span class="pun">,</span><span class="kwd">function</span><span class="pun">(){</span><span class="pln">
    audio</span><span class="pun">.</span><span class="pln">play</span><span class="pun">()</span><span class="pln">
</span><span class="pun">})</span></code></pre>
        <p><strong>23.摇一摇功能</strong></p>
        <p>HTML5 deviceMotion：封装了运动传感器数据的事件，可以获取手机运动状态下的运动加速度等数据。</p>
        <p><strong>24.手机拍照和上传图片</strong></p>
        <p><code>&lt;input type="file"&gt;</code>的accept 属性</p>
<pre class="prettyprint"><code><span class="com">&lt;!-- 选择照片 --&gt;</span><span class="pln">
</span><span class="tag">&lt;input</span><span class="pln"> </span><span class="atn">type</span><span class="pun">=</span><span class="atv">file</span><span class="pln"> </span><span class="atn">accept</span><span class="pun">=</span><span class="atv">"image/*"</span><span class="tag">&gt;</span><span class="pln">
</span><span class="com">&lt;!-- 选择视频 --&gt;</span><span class="pln">
</span><span class="tag">&lt;input</span><span class="pln"> </span><span class="atn">type</span><span class="pun">=</span><span class="atv">file</span><span class="pln"> </span><span class="atn">accept</span><span class="pun">=</span><span class="atv">"video/*"</span><span class="tag">&gt;</span></code></pre>
        <p><strong>使用总结：</strong></p>
        <ul>
            <li>iOS有拍照、录像、选取本地图片功能</li>
            <li>部分android只有选取本地图片功能</li>
            <li>winphone不支持</li>
            <li>input控件默认外观丑陋</li>
        </ul>
        <p><strong>25.消除transition闪屏</strong></p>
<pre class="prettyprint"><code><span class="pun">.</span><span class="pln">css</span><span class="pun">{</span><span class="pln">
    </span><span class="com">/*设置内嵌的元素在 3D 空间如何呈现：保留 3D*/</span><span class="pln">
    </span><span class="pun">-</span><span class="pln">webkit</span><span class="pun">-</span><span class="pln">transform</span><span class="pun">-</span><span class="pln">style</span><span class="pun">:</span><span class="pln"> preserve</span><span class="pun">-</span><span class="lit">3d</span><span class="pun">;</span><span class="pln">
    </span><span class="com">/*（设置进行转换的元素的背面在面对用户时是否可见：隐藏）*/</span><span class="pln">
    </span><span class="pun">-</span><span class="pln">webkit</span><span class="pun">-</span><span class="pln">backface</span><span class="pun">-</span><span class="pln">visibility</span><span class="pun">:</span><span class="pln"> hidden</span><span class="pun">;</span><span class="pln">
</span><span class="pun">}</span></code></pre>
        <p><strong>开启硬件加速</strong></p>
        <ul>
            <li>解决页面闪白</li>
            <li>保证动画流畅</li>
        </ul>
<pre class="prettyprint"><code><span class="pln">  </span><span class="pun">.</span><span class="pln">css </span><span class="pun">{</span><span class="pln">
     </span><span class="pun">-</span><span class="pln">webkit</span><span class="pun">-</span><span class="pln">transform</span><span class="pun">:</span><span class="pln"> translate3d</span><span class="pun">(</span><span class="lit">0</span><span class="pun">,</span><span class="pln"> </span><span class="lit">0</span><span class="pun">,</span><span class="pln"> </span><span class="lit">0</span><span class="pun">);</span><span class="pln">
     </span><span class="pun">-</span><span class="pln">moz</span><span class="pun">-</span><span class="pln">transform</span><span class="pun">:</span><span class="pln"> translate3d</span><span class="pun">(</span><span class="lit">0</span><span class="pun">,</span><span class="pln"> </span><span class="lit">0</span><span class="pun">,</span><span class="pln"> </span><span class="lit">0</span><span class="pun">);</span><span class="pln">
     </span><span class="pun">-</span><span class="pln">ms</span><span class="pun">-</span><span class="pln">transform</span><span class="pun">:</span><span class="pln"> translate3d</span><span class="pun">(</span><span class="lit">0</span><span class="pun">,</span><span class="pln"> </span><span class="lit">0</span><span class="pun">,</span><span class="pln"> </span><span class="lit">0</span><span class="pun">);</span><span class="pln">
     transform</span><span class="pun">:</span><span class="pln"> translate3d</span><span class="pun">(</span><span class="lit">0</span><span class="pun">,</span><span class="pln"> </span><span class="lit">0</span><span class="pun">,</span><span class="pln"> </span><span class="lit">0</span><span class="pun">);</span><span class="pln">
  </span><span class="pun">}</span></code></pre>
        <p>设计高性能CSS3动画的几个要素</p>
        <ul>
            <li>尽可能地使用合成属性transform和opacity来设计CSS3动画</li>
            <li>不使用position的left和top来定位</li>
            <li>利用translate3D开启GPU加速</li>
        </ul>
        <p><strong>26. android 上去掉语音输入按钮</strong></p>
<pre class="prettyprint"><code><span class="pln">input</span><span class="pun">::-</span><span class="pln">webkit</span><span class="pun">-</span><span class="pln">input</span><span class="pun">-</span><span class="pln">speech</span><span class="pun">-</span><span class="pln">button </span><span class="pun">{</span><span class="pln">display</span><span class="pun">:</span><span class="pln"> none</span><span class="pun">}</span></code></pre>
        <p><strong>框架</strong></p>
        <p><strong>1. 移动端基础框架</strong></p>
        <ul>
            <li><strong><a href="http://zeptojs.com/" target="_blank">zepto.js</a></strong>语法与jquery几乎一样，会jquery基本会zepto；</li>
            <li><strong><a href="http://cubiq.org/iscroll-5" target="_blank">iscroll.js</a></strong>解决页面不支持弹性滚动，不支持fixed引起的问题~ 实现下拉刷新，滑屏，缩放等功能；</li>
            <li><strong><a href="http://underscorejs.org/" target="_blank">underscore.js</a></strong>该库提供了一整套函数式编程的实用功能，但是没有扩展任何JavaScript内置对象；</li>
            <li><strong><a href="https://github.com/ftlabs/fastclick" target="_blank">fastclick</a></strong>加快移动端点击响应时间</li>
            <li><strong><a href="http://daneden.github.io/animate.css/" target="_blank">animate.css</a></strong> CSS3动画效果库</li>
        </ul>
        <p><strong>2.滑屏框架</strong></p>
        <p>适合上下滑屏、左右滑屏等滑屏切换页面的效果</p>
        <ul>
            <li><strong><a href="https://github.com/peunzhang/slip.js" target="_blank">slip.js</a></strong></li>
            <li><strong><a href="https://github.com/peunzhang/iSlider" target="_blank">iSlider.js</a></strong></li>
            <li><strong><a href="https://github.com/peunzhang/fullpage" target="_blank">fullpage.js</a></strong></li>
        </ul>
        <p><strong>3.瀑布流框架</strong></p>
        <ul>
            <li><strong><a href="http://masonry.desandro.com/" target="_blank">masonry</a></strong></li>
        </ul>
        <p><strong>工具推荐</strong></p>
        <ul>
            <li><strong><a href="http://caniuse.com/" target="_blank">caniuse</a></strong> 各浏览器支持html5属性查询</li>
            <li><strong><a href="http://paletton.com/#uid=1000u0kllllaFw0g0qFqFg0w0aF" target="_blank">paletton</a></strong> 调色搭配</li>
        </ul>
        <blockquote>
            <p>
                文章源自：ljinkai.github.io/2015/06/06/mobile-web-skill/<br>
                作者：凯凯刘
            </p>
        </blockquote>
    </div>
</div>
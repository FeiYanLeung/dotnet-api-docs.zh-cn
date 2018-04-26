### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a><span data-ttu-id="8544f-101">ImageSourceConverter.ConvertFrom 异常处理代码中的 NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="8544f-101">NullReferenceException in exception handling code from ImageSourceConverter.ConvertFrom</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8544f-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="8544f-102">Details</span></span>|<span data-ttu-id="8544f-103"><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> 异常处理代码中的错误导致了引发不正确的 <xref:System.NullReferenceException?displayProperty=name>，而不是引发计划的异常（例如 <xref:System.IO.DirectoryNotFoundException?displayProperty=name>、<xref:System.IO.FileNotFoundException?displayProperty=name>），此更改改正该错误，使得该方法现在引发正确的异常。默认情况下，所有面向 .NET Framework 4.6.2 和更低版本的应用程序将继续引发 <xref:System.NullReferenceException?displayProperty=name> 以实现兼容性，面向 .NET Framework 4.7 和更高版本的开发人员应看到正确的异常。//使用“x”替换空格（如果适用）</span><span class="sxs-lookup"><span data-stu-id="8544f-103">An error in the exception handling code for <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> caused an incorrect <xref:System.NullReferenceException?displayProperty=name> to be thrown instead of the intended exception (e.g. <xref:System.IO.DirectoryNotFoundException?displayProperty=name>, <xref:System.IO.FileNotFoundException?displayProperty=name>), this change corrects that error so that the method now throws the right exception.By default all applications targeting .NET Framework 4.6.2 and below will continue to throw <xref:System.NullReferenceException?displayProperty=name> for compatibility, developers targeting .NET Framework 4.7 and above should see the right exceptions.// Replace the space with an 'x' if applicable</span></span>|
|<span data-ttu-id="8544f-104">建议</span><span class="sxs-lookup"><span data-stu-id="8544f-104">Suggestion</span></span>|<span data-ttu-id="8544f-105">想要还原为在面向 .NET Framework 4.7 时获取 <xref:System.NullReferenceException?displayProperty=name> 的开发人员可以将以下内容添加/合并到应用程序的 App.config 文件：</span><span class="sxs-lookup"><span data-stu-id="8544f-105">Developers who wish to revert to getting <xref:System.NullReferenceException?displayProperty=name> when targeting .NET Framework 4.7 can add/merge the following to their application's App.config file:</span></span><pre><code class="language-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="8544f-106">范围</span><span class="sxs-lookup"><span data-stu-id="8544f-106">Scope</span></span>|<span data-ttu-id="8544f-107">边缘</span><span class="sxs-lookup"><span data-stu-id="8544f-107">Edge</span></span>|
|<span data-ttu-id="8544f-108">版本</span><span class="sxs-lookup"><span data-stu-id="8544f-108">Version</span></span>|<span data-ttu-id="8544f-109">4.7</span><span class="sxs-lookup"><span data-stu-id="8544f-109">4.7</span></span>|
|<span data-ttu-id="8544f-110">类型</span><span class="sxs-lookup"><span data-stu-id="8544f-110">Type</span></span>|<span data-ttu-id="8544f-111">重定目标</span><span class="sxs-lookup"><span data-stu-id="8544f-111">Retargeting</span></span>|
|<span data-ttu-id="8544f-112">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="8544f-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType></li></ul>|

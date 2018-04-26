### <a name="x509certificate2tostringbool-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="c5859-101">现在当 .NET 无法处理证书时，不会引发 X509Certificate2.ToString(bool)</span><span class="sxs-lookup"><span data-stu-id="c5859-101">X509Certificate2.ToString(bool) does not throw now when .NET cannot handle the certificate</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c5859-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="c5859-102">Details</span></span>|<span data-ttu-id="c5859-103">以前如果为详细参数传递 <code>true</code>，并且安装了 .NET Framework 不支持的证书，将引发此方法。</span><span class="sxs-lookup"><span data-stu-id="c5859-103">Previously, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="c5859-104">现在，该方法将取得成功，并返回省略证书无法访问部分的有效字符串。</span><span class="sxs-lookup"><span data-stu-id="c5859-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>|
|<span data-ttu-id="c5859-105">建议</span><span class="sxs-lookup"><span data-stu-id="c5859-105">Suggestion</span></span>|<span data-ttu-id="c5859-106">应更新任何依赖 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)> 的代码，以希望返回的字符串会排除在某些情况下，API 之前曾引发的某些证书数据（例如公钥、私钥和扩展）。</span><span class="sxs-lookup"><span data-stu-id="c5859-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>|
|<span data-ttu-id="c5859-107">范围</span><span class="sxs-lookup"><span data-stu-id="c5859-107">Scope</span></span>|<span data-ttu-id="c5859-108">边缘</span><span class="sxs-lookup"><span data-stu-id="c5859-108">Edge</span></span>|
|<span data-ttu-id="c5859-109">版本</span><span class="sxs-lookup"><span data-stu-id="c5859-109">Version</span></span>|<span data-ttu-id="c5859-110">4.6</span><span class="sxs-lookup"><span data-stu-id="c5859-110">4.6</span></span>|
|<span data-ttu-id="c5859-111">类型</span><span class="sxs-lookup"><span data-stu-id="c5859-111">Type</span></span>|<span data-ttu-id="c5859-112">运行时</span><span class="sxs-lookup"><span data-stu-id="c5859-112">Runtime</span></span>|
|<span data-ttu-id="c5859-113">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="c5859-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|

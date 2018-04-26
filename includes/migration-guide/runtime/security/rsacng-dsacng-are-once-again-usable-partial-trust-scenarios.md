### <a name="rsacng-and-dsacng-are-once-again-usable-in-partial-trust-scenarios"></a><span data-ttu-id="f8533-101">RSACng 和 DSACng 在部分信任方案中再次可用</span><span class="sxs-lookup"><span data-stu-id="f8533-101">RSACng and DSACng are once again usable in Partial Trust scenarios</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f8533-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="f8533-102">Details</span></span>|<span data-ttu-id="f8533-103">某些情况下 CngLightup（在多个更高级别的加密 API 中使用，例如 <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>）和 <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> 依赖完全信任。</span><span class="sxs-lookup"><span data-stu-id="f8533-103">CngLightup (used in several higher-level crypto apis, such as <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>) and <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> in some cases rely on full trust.</span></span> <span data-ttu-id="f8533-104">其中包括未断言 <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> 权限的 P/Invoke 和 <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> 在其中有 <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> 权限要求的代码路径。</span><span class="sxs-lookup"><span data-stu-id="f8533-104">These include P/Invokes without asserting <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> permissions, and code paths where <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> has permission demands for <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f8533-105">自 .NET Framework 4.6.2 起，CngLightup 尽可能用于切换到 <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f8533-105">Starting with the .NET Framework 4.6.2, CngLightup was used to switch to <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> wherever possible.</span></span> <span data-ttu-id="f8533-106">结果，成功使用 <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> 的部分信任应用开始失败并引发 <xref:System.Security.SecurityException> 异常。此更改添加所需断言，以便所有使用 CngLightup 的函数都有所需权限。</span><span class="sxs-lookup"><span data-stu-id="f8533-106">As a result, partial trust apps that successfully used <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> began to fail and throw <xref:System.Security.SecurityException> exceptions.This change adds the required asserts so that all functions using CngLightup have the required permissions.</span></span>|
|<span data-ttu-id="f8533-107">建议</span><span class="sxs-lookup"><span data-stu-id="f8533-107">Suggestion</span></span>|<span data-ttu-id="f8533-108">如果 .NET Framework 4.6.2 中的此更改对部分信任应用有负面影响，请升级到 .NET Framework 4.7.1。</span><span class="sxs-lookup"><span data-stu-id="f8533-108">If this change in the .NET Framework 4.6.2 has negatively impacted your partial trust apps, upgrade to the .NET Framework 4.7.1.</span></span>|
|<span data-ttu-id="f8533-109">范围</span><span class="sxs-lookup"><span data-stu-id="f8533-109">Scope</span></span>|<span data-ttu-id="f8533-110">边缘</span><span class="sxs-lookup"><span data-stu-id="f8533-110">Edge</span></span>|
|<span data-ttu-id="f8533-111">版本</span><span class="sxs-lookup"><span data-stu-id="f8533-111">Version</span></span>|<span data-ttu-id="f8533-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="f8533-112">4.6.2</span></span>|
|<span data-ttu-id="f8533-113">类型</span><span class="sxs-lookup"><span data-stu-id="f8533-113">Type</span></span>|<span data-ttu-id="f8533-114">运行时</span><span class="sxs-lookup"><span data-stu-id="f8533-114">Runtime</span></span>|
|<span data-ttu-id="f8533-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="f8533-115">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.DSACng.%23ctor(System.Security.Cryptography.CngKey)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.LegalKeySizes?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.%23ctor(System.Security.Cryptography.CngKey)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

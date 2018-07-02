---
title: 在 BizTalk Server 中憑證的已知問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab58264b-2475-4831-9f08-bfbaa293022f
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5291327cfe037a38283a984015c0027b7fdc7c3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969063"
---
# <a name="known-issues-with-certificates-in-biztalk-server"></a><span data-ttu-id="2787b-102">在 BizTalk Server 中使用憑證的已知的問題</span><span class="sxs-lookup"><span data-stu-id="2787b-102">Known Issues with Certificates in BizTalk Server</span></span>
<span data-ttu-id="2787b-103">本節說明管理搭配使用的數位簽章的已知的問題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2787b-103">This section describes known issues with managing digital certificates used with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="general-certificate-issues"></a><span data-ttu-id="2787b-104">一般憑證問題</span><span class="sxs-lookup"><span data-stu-id="2787b-104">General Certificate Issues</span></span>  
  
### <a name="lack-of-connectivity-to-the-certificate-revocation-list-will-cause-a-certificate-to-be-rejected"></a><span data-ttu-id="2787b-105">缺少連線的憑證撤銷清單會遭到拒絕的憑證</span><span class="sxs-lookup"><span data-stu-id="2787b-105">Lack of connectivity to the certificate revocation list will cause a certificate to be rejected</span></span>  
 <span data-ttu-id="2787b-106">這個問題牽涉到下列錯誤: 「 發生驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="2787b-106">This issue involves the following error: “There was an authentication error.</span></span> <span data-ttu-id="2787b-107">發行用來簽署訊息的憑證的憑證授權單位 (CA) 的狀態為不明。 」</span><span class="sxs-lookup"><span data-stu-id="2787b-107">The status of the certification authority (CA) that issued the certificate used to sign the message is unknown."</span></span> <span data-ttu-id="2787b-108">會發生這個錯誤，即使簽署的憑證是有效 MMC 底下檢視時 (使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用者) 上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2787b-108">This error can occur even when the signing certificate is valid when viewed under MMC (using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] user) on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="2787b-109">如果在接收管線中的 S/MIME 解碼器元件上啟用 「 檢查憑證撤銷 」 屬性，會發生此狀況。</span><span class="sxs-lookup"><span data-stu-id="2787b-109">This condition can occur if the "Check Certificate Revocation" property is enabled on the S/MIME decoder component in the receive pipeline.</span></span> <span data-ttu-id="2787b-110">當這個屬性設定為 true 時，BizTalk Server 會嘗試查詢的 「 憑證撤銷清單 (CRL) 」，以查看是否已撤銷的連入的憑證。</span><span class="sxs-lookup"><span data-stu-id="2787b-110">When this property is set to true, BizTalk Server will try to query the Certificate Revocation List (CRL) to see if the incoming certificate has been revoked.</span></span> <span data-ttu-id="2787b-111">它並不重要未撤銷憑證本身。</span><span class="sxs-lookup"><span data-stu-id="2787b-111">It does not matter if the certificate itself is not revoked.</span></span> <span data-ttu-id="2787b-112">如果 BizTalk Server 無法查詢對應的 CRL，因為連線發生問題，也不會接受憑證。</span><span class="sxs-lookup"><span data-stu-id="2787b-112">If BizTalk Server cannot query the corresponding CRL because of connectivity issues, it will not accept the certificate.</span></span> <span data-ttu-id="2787b-113">若要疑難排解這個錯誤，顯示憑證的內容，請按兩下您所使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="2787b-113">To troubleshoot this error, display the certificate's properties by double-clicking the certificate that you used.</span></span> <span data-ttu-id="2787b-114">在其 [詳細資料] 索引標籤中，您會看到 [欄位] 清單中的屬性 [CRL 發佈點]。</span><span class="sxs-lookup"><span data-stu-id="2787b-114">In its Details tab, you will see the attribute "CRL Distribution Point" in the field list.</span></span> <span data-ttu-id="2787b-115">應該會有數個在這個屬性中的 Url 指向您的 CA 伺服器上的 CRL。</span><span class="sxs-lookup"><span data-stu-id="2787b-115">There should be several URLs in this attribute that point to the CRL on your CA server.</span></span> <span data-ttu-id="2787b-116">BizTalk server 必須能夠存取任何這些 Url，以擷取 CRL。</span><span class="sxs-lookup"><span data-stu-id="2787b-116">The BizTalk server must be able to access any of these URLs to retrieve the CRL.</span></span> <span data-ttu-id="2787b-117">否則，撤銷檢查會失敗並出現上述錯誤，將會公佈。</span><span class="sxs-lookup"><span data-stu-id="2787b-117">Otherwise, the revocation checking will fail and the above error will be posted.</span></span>  
  
### <a name="the-other-people-certificate-store-is-not-initialized-until-accessed"></a><span data-ttu-id="2787b-118">直到存取未初始化的其他人 」 憑證存放區</span><span class="sxs-lookup"><span data-stu-id="2787b-118">The Other People Certificate store is not initialized until accessed</span></span>  
 <span data-ttu-id="2787b-119">當您嘗試新增或修改傳送/接收埠/位置使用時，這個問題牽涉到下列憑證存放區錯誤[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理員主控台從遠端: 「 無法開啟憑證存放區 」。</span><span class="sxs-lookup"><span data-stu-id="2787b-119">This issue involves the following certificate store error when you try to add or modify send/receive ports/locations using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrator console remotely: “Could not open certificate store.”</span></span> <span data-ttu-id="2787b-120">和 「 系統找不到指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="2787b-120">and “The system cannot find the file specified.</span></span> <span data-ttu-id="2787b-121">（系統） 」。</span><span class="sxs-lookup"><span data-stu-id="2787b-121">(System)”.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2787b-122">您可以修改使用 [管理] 主控台，如果您直接登入這些成品[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2787b-122">You can modify these artifacts using the administration console if you log on directly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="2787b-123">在新安裝的電腦上**其他人 」 憑證**除非您一次存取未初始化存放區。</span><span class="sxs-lookup"><span data-stu-id="2787b-123">On a newly installed computer, the **Other People Certificate** store is not initialized unless you access it once.</span></span> <span data-ttu-id="2787b-124">群組在設定期間，您可以初始化這**其他人 」 憑證**儲存，並因此已完成的群組設定的電腦上未看到此錯誤。</span><span class="sxs-lookup"><span data-stu-id="2787b-124">During the group configuration, you can initialize this **Other People Certificate** store, and as a result not see this error on a computer on which group configuration has been done.</span></span>  
  
### <a name="biztalk-server-only-supports-one-personal-certificate-for-each-biztalk-group"></a><span data-ttu-id="2787b-125">BizTalk Server 只支援一個個人的憑證，針對每個 BizTalk 群組</span><span class="sxs-lookup"><span data-stu-id="2787b-125">BizTalk Server only supports one personal certificate for each BizTalk group</span></span>  
 <span data-ttu-id="2787b-126">BizTalk 群組使用的個人憑證是由設定 BizTalk 群組屬性中的 個人憑證的指紋指定。</span><span class="sxs-lookup"><span data-stu-id="2787b-126">The personal certificate that is used by the BizTalk group is specified by setting the thumbprint of the personal certificate in the BizTalk group properties.</span></span> <span data-ttu-id="2787b-127">企業、 部門、 集線器或另一個業務單位，可以代表 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="2787b-127">A BizTalk group can represent an enterprise, a department, a hub, or another business unit.</span></span>  
  
## <a name="as2-certificate-issues"></a><span data-ttu-id="2787b-128">AS2 的憑證問題</span><span class="sxs-lookup"><span data-stu-id="2787b-128">AS2 Certificate Issues</span></span>  
  
### <a name="the-as2-decoder-will-not-validate-that-a-certificate-is-configured-on-the-host-or-for-the-destination-party"></a><span data-ttu-id="2787b-129">AS2 解碼器將不會驗證憑證已在主機或目的合作對象</span><span class="sxs-lookup"><span data-stu-id="2787b-129">The AS2 decoder will not validate that a certificate is configured on the host or for the destination party</span></span>  
 <span data-ttu-id="2787b-130">只要憑證存放區中已設定訊息的私用憑證，AS2 解碼器就會解密訊息。</span><span class="sxs-lookup"><span data-stu-id="2787b-130">The AS2 decoder will decrypt a message as long as the private certificate for that message is configured in the certificate store.</span></span> <span data-ttu-id="2787b-131">不過，AS2 解碼器將不會驗證解密憑證是否與主控件上設定的憑證相同。</span><span class="sxs-lookup"><span data-stu-id="2787b-131">However, the AS2 decoder will not validate that the decryption certificate is the same as the certificate configured on the host.</span></span> <span data-ttu-id="2787b-132">收到的訊息可以使用一個以上的憑證加密。</span><span class="sxs-lookup"><span data-stu-id="2787b-132">The received message can be encrypted with more than one certificate.</span></span>  
  
### <a name="biztalk-server-will-be-unable-to-decrypt-a-message-saved-in-wire-format-if-the-certificate-is-not-valid"></a><span data-ttu-id="2787b-133">BizTalk Server 將無法解密以電傳格式儲存，如果憑證不是有效的訊息</span><span class="sxs-lookup"><span data-stu-id="2787b-133">BizTalk Server will be unable to decrypt a message saved in wire format if the certificate is not valid</span></span>  
 <span data-ttu-id="2787b-134">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="2787b-134">**Symptom**</span></span>  
  
 <span data-ttu-id="2787b-135">BizTalk Server 無法解密以電傳格式儲存在不可否認性資料庫中的內送 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="2787b-135">BizTalk Server is unable to decrypt an inbound AS2 message that was saved in wire format in the non-repudiation database.</span></span>  
  
 <span data-ttu-id="2787b-136">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="2787b-136">**Possible Cause**</span></span>  
  
 <span data-ttu-id="2787b-137">解密訊息時所需的憑證已過期或已撤銷。</span><span class="sxs-lookup"><span data-stu-id="2787b-137">The certificate required to decrypt the message has expired or been revoked.</span></span> <span data-ttu-id="2787b-138">當 AS2 訊息儲存在不可否認性資料庫一段時間後，就可能會發生這種狀況。</span><span class="sxs-lookup"><span data-stu-id="2787b-138">This is more likely to occur if a certain period of time has elapsed since the AS2 message was saved in the non-repudiation database.</span></span> <span data-ttu-id="2787b-139">這時您可能無法立即存取訊息的有效憑證。</span><span class="sxs-lookup"><span data-stu-id="2787b-139">If this occurs, you may not have immediate access to a valid certificate for the message.</span></span>  
  
 <span data-ttu-id="2787b-140">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="2787b-140">**Resolution**</span></span>  
  
 <span data-ttu-id="2787b-141">取得有效憑證來解密訊息。</span><span class="sxs-lookup"><span data-stu-id="2787b-141">Acquire a valid certificate for decrypting the message.</span></span>  
  
### <a name="if-an-as2-message-cannot-be-decrypted-the-problem-may-be-fixed-by-re-importing-the-certificate"></a><span data-ttu-id="2787b-142">如果無法解密 AS2 訊息，問題便可以解決重新匯入憑證</span><span class="sxs-lookup"><span data-stu-id="2787b-142">If an AS2 message cannot be decrypted, the problem may be fixed by re-importing the certificate</span></span>  
 <span data-ttu-id="2787b-143">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="2787b-143">**Symptom**</span></span>  
  
 <span data-ttu-id="2787b-144">AS2 解碼器發生例外狀況時它會嘗試解密 AS2 訊息，擲回下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="2787b-144">The AS2 Decoder encounters an exception when it attempts to decrypt an AS2 message, throwing the following error:</span></span>  
  
```  
"The AS2 Decoder encountered an exception during processing. Details of the message and exception are as follows:   
   AS2-From:"PARTNER" AS2-To:"HOME" MessageID:"<137706.1178060412333@servername>"   
   MessageType: "unknown" Exception:"An error occurred when decrypting an AS2 message."  
System.ArgumentNullException: Value cannot be null.  
Parameter name: PayloadContentType  
at Microsoft.BizTalk.Edi.Reporting.Common.Utilities.ValidateArgument(Object o,  
String parameterName, Boolean isEmptyStringValidationRequired)  
at Microsoft.BizTalk.EdiInt.Reporting.AS2MessageActivity.ValidateParameters()  
at Microsoft.BizTalk.EdiInt.Reporting.AS2MessageActivity.Create()"  
  
```  
  
 <span data-ttu-id="2787b-145">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="2787b-145">**Possible Cause**</span></span>  
  
 <span data-ttu-id="2787b-146">用來解密 AS2 訊息的憑證必須重新載入「個人存放區」。</span><span class="sxs-lookup"><span data-stu-id="2787b-146">The certificate used to decrypt the AS2 message needs to be reloaded into the Personal Store.</span></span>  
  
 <span data-ttu-id="2787b-147">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="2787b-147">**Resolution**</span></span>  
  
 <span data-ttu-id="2787b-148">從 [個人存放區] 刪除現有的憑證，然後使用 [憑證匯入精靈] 將憑證重新匯入 [個人存放區]。</span><span class="sxs-lookup"><span data-stu-id="2787b-148">Delete the existing certificate from the Personal Store, and then re-import the certificate into the Personal Store using the Certificate Import Wizard.</span></span> <span data-ttu-id="2787b-149">執行這項操作以滑鼠右鍵按一下**憑證**下方的資料夾**個人存放區**，指向**所有工作**，，然後按一下**匯入**。</span><span class="sxs-lookup"><span data-stu-id="2787b-149">Do so by right-clicking the **Certificate** folder under the **Personal Store**, pointing to **All Tasks**, and then clicking **Import**.</span></span>  
  
### <a name="use-the-same-logon-for-the-in-process-host-instance-and-the-isolated-host-instance-to-ensure-that-personal-store-is-recognized"></a><span data-ttu-id="2787b-150">使用內含式主控件執行個體和外掛式主控件執行個體相同的登入，以確保可辨識該個人存放區</span><span class="sxs-lookup"><span data-stu-id="2787b-150">Use the same logon for the in-process host instance and the isolated host instance to ensure that personal store is recognized</span></span>  
 <span data-ttu-id="2787b-151">只有在針對其登入認證與主控件執行個體相關聯的使用者載入使用者設定檔時，個人憑證存放區才能用於訊息處理。</span><span class="sxs-lookup"><span data-stu-id="2787b-151">The Personal certificate store will be available for message processing only if the user profile is loaded for the user whose logon credentials are associated with the host instance.</span></span> <span data-ttu-id="2787b-152">個人存放區是用於簽章和解密憑證 (使用者專屬的私密金鑰)。</span><span class="sxs-lookup"><span data-stu-id="2787b-152">The Personal store is used for signing and decryption certificates (the user's own private key).</span></span> <span data-ttu-id="2787b-153">預設會為內含式主控件執行個體載入使用者設定檔，但是不會為外掛式主控件執行個體載入使用者設定檔。</span><span class="sxs-lookup"><span data-stu-id="2787b-153">The user profile is loaded by default for the in-process host instance; however, the user profile is not loaded by default for the isolated host instance.</span></span> <span data-ttu-id="2787b-154">您可以讓應用程式針對外掛式主控件載入使用者設定檔。</span><span class="sxs-lookup"><span data-stu-id="2787b-154">You can have an application load the user profile for the isolated host.</span></span> <span data-ttu-id="2787b-155">或者，您也可以為內含式主控件執行個體和外掛式主控件執行個體使用相同的登入，以解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="2787b-155">Alternatively, you can work around this issue by using the same logon for the in-process host instance and the isolated host instance.</span></span>  
  
 <span data-ttu-id="2787b-156">除了由應用程式載入使用者設定檔，您也可以建立空的服務來載入設定檔。</span><span class="sxs-lookup"><span data-stu-id="2787b-156">Instead of having an application load the user profile, you can create an empty service to load the profile.</span></span> <span data-ttu-id="2787b-157">如需建立空的服務的詳細資訊，請參閱[如何： 建立 Windows 服務](http://go.microsoft.com/fwlink/?LinkId=155149)(http://go.microsoft.com/fwlink/?LinkId=155149) Visual Studio 的 [說明] 中。</span><span class="sxs-lookup"><span data-stu-id="2787b-157">For more information about creating an empty service, see [How to: Create Windows Services](http://go.microsoft.com/fwlink/?LinkId=155149) (http://go.microsoft.com/fwlink/?LinkId=155149) in Visual Studio Help.</span></span>  
  
 <span data-ttu-id="2787b-158">建立空的服務，來載入設定檔之後, 繼續執行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2787b-158">After creating the empty service to load the profile, proceed as follows:</span></span>  
  
1.  <span data-ttu-id="2787b-159">按一下 [**開始**，然後按一下**執行**以開啟**執行**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2787b-159">Click **Start**, and then click **Run** to open the **Run** dialog box.</span></span>  
  
2.  <span data-ttu-id="2787b-160">在**執行** 對話方塊中，輸入**service.msc**然後按**ENTER**以開啟**服務**MMC 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="2787b-160">In the **Run** dialog box, type **service.msc** and press **ENTER** to open the **Services** MMC snap-in.</span></span>  
  
3.  <span data-ttu-id="2787b-161">開啟**屬性**如您所建立的服務 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2787b-161">Open the **Properties** dialog box for the service you created.</span></span> <span data-ttu-id="2787b-162">以滑鼠右鍵按一下服務，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="2787b-162">Right-click the service and select **Properties**.</span></span>  
  
4.  <span data-ttu-id="2787b-163">按一下 **登入**索引標籤上，選取**這個帳戶**，然後輸入用於外掛式主控件執行個體的登入名稱。</span><span class="sxs-lookup"><span data-stu-id="2787b-163">Click the **Log On** tab, select **This Account**, and then enter the logon name used for the isolated host instance.</span></span>  
  
5.  <span data-ttu-id="2787b-164">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="2787b-164">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="2787b-165">以手動方式啟動服務以載入該登入使用者的使用者設定檔。</span><span class="sxs-lookup"><span data-stu-id="2787b-165">Manually start the service to load the user profile for that logon user.</span></span>  
  
### <a name="the-key-usage-attribute-of-a-certificate-must-match-the-certificates-use"></a><span data-ttu-id="2787b-166">憑證的金鑰使用方式屬性必須符合憑證使用方式</span><span class="sxs-lookup"><span data-stu-id="2787b-166">The Key Usage attribute of a certificate must match the certificate's use</span></span>  
 <span data-ttu-id="2787b-167">AS2 傳輸所使用的憑證必須有憑證預定使用方式的必要屬性。</span><span class="sxs-lookup"><span data-stu-id="2787b-167">Certificates used for AS2 transport must have the attributes required for their intended use.</span></span> <span data-ttu-id="2787b-168">針對簽署和簽章驗證，憑證的 [金鑰使用方式] 屬性必須是 [數位簽章]。</span><span class="sxs-lookup"><span data-stu-id="2787b-168">For signing and signature verification, the Key Usage attribute of the certificate must be Digital Signature.</span></span> <span data-ttu-id="2787b-169">針對加密和解密，憑證的 [金鑰使用方式] 屬性必須是 [資料編密] 或 [金鑰編密]。</span><span class="sxs-lookup"><span data-stu-id="2787b-169">For encryption and decryption, the Key Usage attribute of the certificate must be Data Encipherment or Key Encipherment.</span></span> <span data-ttu-id="2787b-170">您可以按兩下憑證，然後按一下驗證金鑰使用方法屬性**詳細資料**索引標籤中**憑證** 對話方塊中，並檢查**金鑰使用方法**欄位.</span><span class="sxs-lookup"><span data-stu-id="2787b-170">You can verify the Key Usage attribute by double-clicking the certificate, clicking the **Details** tab in the **Certificate** dialog box, and checking the **Key Usage** field.</span></span>  
  
### <a name="the-certificate-resolution-list-will-be-verified-for-an-outgoing-mdn-if-the-as2-to-property-is-not-set-for-the-party"></a><span data-ttu-id="2787b-171">如果未設定合作對象的 AS2-To 屬性，則會針對外寄 MDN 驗證憑證解析清單</span><span class="sxs-lookup"><span data-stu-id="2787b-171">The certificate resolution list will be verified for an outgoing MDN if the AS2-To property is not set for the party</span></span>  
 <span data-ttu-id="2787b-172">在外寄 MDN 的預設協議中，會執行憑證解析清單驗證。</span><span class="sxs-lookup"><span data-stu-id="2787b-172">In the default agreement for an outgoing MDN, the certificate resolution list verification is performed.</span></span> <span data-ttu-id="2787b-173">如果您不要執行此驗證，請確認已設定正確的 AS2-To 合作對象屬性，以便解析接收的合作對象並判斷合作對象屬性。</span><span class="sxs-lookup"><span data-stu-id="2787b-173">If you do not want this verification to be performed, verify that the correct AS2-To party property is set, so the receiving party can be resolved and the party properties can be determined.</span></span> <span data-ttu-id="2787b-174">如此一來，便不會使用預設協議 (會提示要驗證憑證解析清單)。</span><span class="sxs-lookup"><span data-stu-id="2787b-174">If so, the default agreement that prompts verification of the certificate resolution list will not be used.</span></span> <span data-ttu-id="2787b-175">您也將需要停用 AS2 合作對象屬性 [一般] 頁面上的 [檢查憑證撤銷清單] 屬性。</span><span class="sxs-lookup"><span data-stu-id="2787b-175">You will also need to disable the Check Certification Revocation List property on the General page of the AS2 party properties.</span></span>
---
title: 最佳做法來管理 Certificates2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71fa00cc-2e0c-46b3-ae62-f130a5b5f4f5
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e2b79e2a0d7e4758ac87503f4bfac122c9ee215
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994783"
---
# <a name="best-practices-for-managing-certificates"></a><span data-ttu-id="ddcef-102">管理憑證的最佳作法</span><span class="sxs-lookup"><span data-stu-id="ddcef-102">Best Practices for Managing Certificates</span></span>
<span data-ttu-id="ddcef-103">本節提供在您的 Microsoft BizTalk Server 環境中管理憑證的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="ddcef-103">This section provides best practices for managing certificates in your Microsoft BizTalk Server environment.</span></span>  
  
## <a name="assess-and-plan-your-use-of-certificates"></a><span data-ttu-id="ddcef-104">評估及規劃您使用的憑證</span><span class="sxs-lookup"><span data-stu-id="ddcef-104">Assess and Plan Your Use of Certificates</span></span>  
 <span data-ttu-id="ddcef-105">**執行環境的威脅模型分析**</span><span class="sxs-lookup"><span data-stu-id="ddcef-105">**Do a Threat Model Analysis of your environment**</span></span>  
  
- <span data-ttu-id="ddcef-106">執行您環境的「威脅模型分析」(TMA) 以判斷簽章或加密憑證是否有助於減輕安全性威脅。</span><span class="sxs-lookup"><span data-stu-id="ddcef-106">Do a Threat Model Analysis (TMA) of your environment to determine whether signing or encryption certificates will help you mitigate security threats.</span></span>  
  
  <span data-ttu-id="ddcef-107">**建立與夥伴的公開金鑰憑證的計劃**</span><span class="sxs-lookup"><span data-stu-id="ddcef-107">**Create a plan for public key certificates with partners**</span></span>  
  
- <span data-ttu-id="ddcef-108">建立將公開金鑰憑證來傳送和接收來自夥伴的公開金鑰憑證的計劃。</span><span class="sxs-lookup"><span data-stu-id="ddcef-108">Create a plan for sending public key certificates to and receiving public key certificates from partners.</span></span> <span data-ttu-id="ddcef-109">如果您沒有使用簽章憑證進行合作對象解析，則可以將公用憑證附加到訊息；在此情況下，您的系統並不需要預先準備憑證的複本。</span><span class="sxs-lookup"><span data-stu-id="ddcef-109">If you are not using signing certificates for party resolution, the public certificate can be attached to the message, in which case you do not need a copy of the certificate in your system beforehand.</span></span>  
  
  <span data-ttu-id="ddcef-110">**與合作夥伴的指導方針建立提交公開金鑰**</span><span class="sxs-lookup"><span data-stu-id="ddcef-110">**Establish guidelines with partners for submitting public keys**</span></span>  
  
- <span data-ttu-id="ddcef-111">在與夥伴的「服務等級協議」(SLA) 內容中，建立提交公開金鑰的指導方針，在他們的憑證即將到期時，以及在他們撤銷憑證時通知您。</span><span class="sxs-lookup"><span data-stu-id="ddcef-111">As part of your Service Level Agreement (SLA) with your partner, establish guidelines for submitting public keys, notifying you when their certificates are about to expire, and notifying you when they revoke a certificate.</span></span>  
  
## <a name="install-certificates"></a><span data-ttu-id="ddcef-112">安裝憑證</span><span class="sxs-lookup"><span data-stu-id="ddcef-112">Install Certificates</span></span>  
 <span data-ttu-id="ddcef-113">**設定的間隔下載憑證撤銷清單**</span><span class="sxs-lookup"><span data-stu-id="ddcef-113">**Download the certificate revocation list at set intervals**</span></span>  
  
- <span data-ttu-id="ddcef-114">下載從您的憑證授權單位 (CA) 憑證撤銷清單 (CRL) 設定的間隔。</span><span class="sxs-lookup"><span data-stu-id="ddcef-114">Download the certificate revocation list (CRL) from your certification authority (CA) at set intervals.</span></span> <span data-ttu-id="ddcef-115">我們建議一週下載一次。</span><span class="sxs-lookup"><span data-stu-id="ddcef-115">We recommend doing this once a week.</span></span> <span data-ttu-id="ddcef-116">如果 BizTalk 伺服器所加入的網域有 CA 存在，便會自動下載 CRL。</span><span class="sxs-lookup"><span data-stu-id="ddcef-116">The CRLs are downloaded automatically if there is a CA for the domain in which the BizTalk servers are joined.</span></span>  
  
  <span data-ttu-id="ddcef-117">**驗證簽章憑證**</span><span class="sxs-lookup"><span data-stu-id="ddcef-117">**Verify signing certificates**</span></span>  
  
- <span data-ttu-id="ddcef-118">您務必要根據憑證撤銷清單驗證簽章憑證。</span><span class="sxs-lookup"><span data-stu-id="ddcef-118">Make sure you verify the signing certificates against the certificate revocation list.</span></span> <span data-ttu-id="ddcef-119">如需如何驗證簽章憑證的詳細資訊，請參閱[如何設定 MIME/SMIME 解碼器管線元件](http://go.microsoft.com/fwlink/?LinkId=155145)(<http://go.microsoft.com/fwlink/?LinkId=155145>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="ddcef-119">For more information about how to verify the signing certificates, see [How to Configure the MIME/SMIME Decoder Pipeline Component](http://go.microsoft.com/fwlink/?LinkId=155145) (<http://go.microsoft.com/fwlink/?LinkId=155145>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
  <span data-ttu-id="ddcef-120">**管理憑證與合作夥伴**</span><span class="sxs-lookup"><span data-stu-id="ddcef-120">**Manage certificates with partners**</span></span>  
  
- <span data-ttu-id="ddcef-121">將憑證管理納入夥伴管理實務的環節。</span><span class="sxs-lookup"><span data-stu-id="ddcef-121">Make certificate management part of your partner management practices.</span></span> <span data-ttu-id="ddcef-122">在從 BizTalk Server 環境中新增或移除合作對象時，建議您新增或移除與該夥伴相關聯的憑證。</span><span class="sxs-lookup"><span data-stu-id="ddcef-122">When you add or remove a party from the BizTalk Server environment, we recommend that you add or remove the certificates associated with that partner.</span></span>  
  
  <span data-ttu-id="ddcef-123">**移除主控件執行個體前移除憑證**</span><span class="sxs-lookup"><span data-stu-id="ddcef-123">**Remove certificates before removing a host instance**</span></span>  
  
- <span data-ttu-id="ddcef-124">從 BizTalk Server 移除主控件執行個體前，請先移除主控件執行個體執行時所用帳戶的個人存放區中的憑證。</span><span class="sxs-lookup"><span data-stu-id="ddcef-124">Before removing a host instance from a BizTalk server, remove the certificates in the personal store of the account under which the host instance is running.</span></span>  
  
## <a name="configure-biztalk-server-to-use-certificates-for-mimesmime"></a><span data-ttu-id="ddcef-125">設定 BizTalk Server 使用 MIME/SMIME 憑證</span><span class="sxs-lookup"><span data-stu-id="ddcef-125">Configure BizTalk Server to Use Certificates for MIME/SMIME</span></span>  
 <span data-ttu-id="ddcef-126">**避免阻斷服務攻擊，數位簽章**</span><span class="sxs-lookup"><span data-stu-id="ddcef-126">**Avoid denial of service attacks for digital signatures**</span></span>  
  
- <span data-ttu-id="ddcef-127">決定您想要的郵件，當 BizTalk Server 無法驗證數位簽章。</span><span class="sxs-lookup"><span data-stu-id="ddcef-127">Determine what you want to do with messages when BizTalk Server cannot validate the digital signature.</span></span> <span data-ttu-id="ddcef-128">設定接收埠上的 [驗證] 屬性，有助於防止阻絕服務攻擊。</span><span class="sxs-lookup"><span data-stu-id="ddcef-128">Setting the Authentication property on the receive port will help prevent denial of service attacks.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="ddcef-129">驗證-捨棄訊息並驗證-保留訊息的接收埠上的旗標需要正確地設定 「 合作對象解析 」 管線元件和合作對象 BizTalk Server 中定義。</span><span class="sxs-lookup"><span data-stu-id="ddcef-129">The Authentication - Drop messages and Authentication - Keep messages flags on the receive port require that the Party Resolution pipeline component be configured correctly, and that the parties are defined in BizTalk Server.</span></span> <span data-ttu-id="ddcef-130">如需詳細資訊，請參閱 <<c0> [ 合作對象解析管線元件](http://go.microsoft.com/fwlink/?LinkId=155146)(<http://go.microsoft.com/fwlink/?LinkId=155146>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="ddcef-130">For more information, see [Party Resolution Pipeline Component](http://go.microsoft.com/fwlink/?LinkId=155146) (<http://go.microsoft.com/fwlink/?LinkId=155146>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
  <span data-ttu-id="ddcef-131">**建立個別的加密和未加密的訊息接收位置**</span><span class="sxs-lookup"><span data-stu-id="ddcef-131">**Create separate receive locations for encrypted and unencrypted messages**</span></span>  
  
- <span data-ttu-id="ddcef-132">如果您打算從某些夥伴接收 MIME 加密訊息，並從其他夥伴接收未加密的訊息，請在不同的主控件中，為加密和未加密的訊息分別建立接收位置。</span><span class="sxs-lookup"><span data-stu-id="ddcef-132">If you plan to receive MIME-encrypted messages from some partners and unencrypted messages from other partners, create separate receive locations in different hosts for encrypted and unencrypted messages.</span></span> <span data-ttu-id="ddcef-133">當您預期只有 MIME 加密訊息時的 [允許非 MIME 訊息] 選項則會在解碼 MIME/SMIME 管線元件，為 [否] 中設定</span><span class="sxs-lookup"><span data-stu-id="ddcef-133">When you expect only MIME-encrypted messages, configure the Allow Non MIME Message option in the Decode MIME/SMIME pipeline component to No.</span></span>  
  
## <a name="configure-a-biztalk-adapter-to-use-certificates"></a><span data-ttu-id="ddcef-134">設定 BizTalk 配接器使用的憑證</span><span class="sxs-lookup"><span data-stu-id="ddcef-134">Configure a BizTalk Adapter to Use Certificates</span></span>  
 <span data-ttu-id="ddcef-135">**測試目標網站的連接**</span><span class="sxs-lookup"><span data-stu-id="ddcef-135">**Test your connection to the target Web site**</span></span>  
  
- <span data-ttu-id="ddcef-136">如果您使用 SSL，請確定您可以連接到目標網站，使用 Microsoft Internet Explorer® 再嘗試連線到目標網站，使用 HTTP 或 SOAP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="ddcef-136">If you are using SSL, ensure that you can connect to the target Web site with Microsoft Internet Explorer® before attempting to connect to the target Web site with the HTTP or SOAP transports.</span></span> <span data-ttu-id="ddcef-137">請確認當您連接到目標網站時，會在 Internet Explorer 中顯示任何對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ddcef-137">Verify that no dialog boxes are displayed in Internet Explorer when you connect to the target Web site.</span></span> <span data-ttu-id="ddcef-138">BizTalk Server 並沒有任何機制互動與連接到目標網站時，可能會顯示任何對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ddcef-138">BizTalk Server has no mechanism for interfacing with any dialog boxes that might be displayed when connecting to the target web site.</span></span> <span data-ttu-id="ddcef-139">如果目標網站名稱不符合指定 SSL 憑證中網站的名稱，或針對 SSL 憑證的根憑證授權單位不是適當的信任根憑證，可能會由 Internet Explorer 顯示對話方塊授權單位存放區。</span><span class="sxs-lookup"><span data-stu-id="ddcef-139">A dialog box may be displayed by Internet Explorer if the target Web site name does not match the name specified for the Web site in the SSL certificate or if the Root Certification Authority for the SSL certificate is not in the appropriate Trusted Root Certification Authorities store.</span></span>  
  
  <span data-ttu-id="ddcef-140">**使用 SSL 診斷工具分析 SSL 連接問題**</span><span class="sxs-lookup"><span data-stu-id="ddcef-140">**Use the SSL Diagnostics tool to analyze SSL connection issues**</span></span>  
  
- <span data-ttu-id="ddcef-141">SSL 診斷工具是 IIS Diagnostics Toolkit 的一個選用元件。</span><span class="sxs-lookup"><span data-stu-id="ddcef-141">The SSL Diagnostics tool is an optional component of the IIS Diagnostics Toolkit.</span></span> <span data-ttu-id="ddcef-142">您可以下載 IIS Diagnostics Toolkit，從[Internet Information Services 診斷工具](http://go.microsoft.com/fwlink/?LinkID=64426)網頁 (http://go.microsoft.com/fwlink/?LinkID=64426)。</span><span class="sxs-lookup"><span data-stu-id="ddcef-142">You can download the IIS Diagnostics Toolkit from the [Internet Information Services Diagnostics Tools](http://go.microsoft.com/fwlink/?LinkID=64426) page (http://go.microsoft.com/fwlink/?LinkID=64426).</span></span>  
  
## <a name="exporting-a-certificate-from-one-biztalk-group-to-another"></a><span data-ttu-id="ddcef-143">將憑證從一個 BizTalk 群組匯出到另一個</span><span class="sxs-lookup"><span data-stu-id="ddcef-143">Exporting a Certificate from One BizTalk Group to Another</span></span>  
 <span data-ttu-id="ddcef-144">**確定匯入的憑證使用針對其預定用途**</span><span class="sxs-lookup"><span data-stu-id="ddcef-144">**Ensure that an imported certificate is being used for its intended purpose**</span></span>  
  
-   <span data-ttu-id="ddcef-145">如果您匯入到群組中的憑證，匯入的憑證必須符合其預期用途的使用方式屬性。</span><span class="sxs-lookup"><span data-stu-id="ddcef-145">If you import a certificate into a group, the imported certificate must have a usage property that is consistent with its intended use.</span></span> <span data-ttu-id="ddcef-146">若要查看使用方式 屬性，連按兩下中的憑證**憑證管理主控台**介面，然後按一下**詳細資料**索引標籤**憑證** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ddcef-146">To check the usage property, double-click the certificate in the **Certificates Management Console** interface, and then click the **Details** tab of the **Certificate** dialog box.</span></span> <span data-ttu-id="ddcef-147">然後按一下**所有**選項**顯示**下拉式清單，然後按一下以選取**金鑰使用方法**及/或**增強金鑰使用方法**欄位若要確認預定的目的。</span><span class="sxs-lookup"><span data-stu-id="ddcef-147">Then click the **All** option for the **Show** drop-down list, and then click to select the **Key Usage** and/or **Enhanced Key Usage** fields to verify the intended purpose.</span></span> <span data-ttu-id="ddcef-148">如果 BizTalk Server 會嘗試使用其預定用途以外的憑證會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="ddcef-148">If BizTalk Server attempts to use a certificate for other than its intended purpose a runtime error will occur.</span></span>
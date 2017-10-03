---
title: "使用 MMC 匯入憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, public keys
- certificates, private keys
- importing certificates
- public keys
- private keys
- certificates, importing
ms.assetid: 58fb1711-e295-4aa6-902e-e28e4a2cd921
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6030b711e0fd48d2632ff84428e1cb9ffc6e0402
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="importing-certificates-using-mmc"></a><span data-ttu-id="1d15e-102">使用 MMC 匯入憑證</span><span class="sxs-lookup"><span data-stu-id="1d15e-102">Importing Certificates Using MMC</span></span>
<span data-ttu-id="1d15e-103">本主題描述如何匯入的數位憑證[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]用以驗證交易夥伴、 解密內送訊息，或是加密或簽署外寄訊息。</span><span class="sxs-lookup"><span data-stu-id="1d15e-103">This topic describes how to import a digital certificate that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] uses to authenticate a trading partner, decrypt an incoming message, or encrypt or sign an outgoing message.</span></span>  
  
 <span data-ttu-id="1d15e-104">此程序使用 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC) 的「憑證」嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="1d15e-104">This procedure uses the Certificates snap-in for the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC).</span></span> <span data-ttu-id="1d15e-105">此一手動程序將憑證匯入憑證存放區，並必須設定個別憑證的使用方式。</span><span class="sxs-lookup"><span data-stu-id="1d15e-105">This manual process imports a certificate into the certificate store, requiring you to configure certificate use separately.</span></span> <span data-ttu-id="1d15e-106">您也可以使用 CertWizard 公用程式匯入憑證。CertWizard 工具可為您自動設定憑證的使用方式。</span><span class="sxs-lookup"><span data-stu-id="1d15e-106">You can also import a certificate by using the CertWizard utility that automatically configures certificate use for you.</span></span>  
  
 <span data-ttu-id="1d15e-107">若要匯入私用憑證，您必須以 BizTalk 主控件執行所用的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="1d15e-107">To import private certificates, you must use the user accounts under which the BizTalk Hosts run.</span></span>  
  
### <a name="to-import-a-public-key-certificate"></a><span data-ttu-id="1d15e-108">匯入公開金鑰憑證</span><span class="sxs-lookup"><span data-stu-id="1d15e-108">To import a public-key certificate</span></span>  
  
1.  <span data-ttu-id="1d15e-109">將公開金鑰 (.cer) 憑證檔案複製到目的伺服器硬碟上的位置。</span><span class="sxs-lookup"><span data-stu-id="1d15e-109">Copy the public-key (.cer) certificate file to a location on the hard disk of the server to which you are copying certificates.</span></span>  
  
2.  <span data-ttu-id="1d15e-110">按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]**管理主控台**.</span><span class="sxs-lookup"><span data-stu-id="1d15e-110">Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.</span></span>  
  
3.  <span data-ttu-id="1d15e-111">在[!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)]管理主控台中，展開 **憑證 （本機電腦）**。</span><span class="sxs-lookup"><span data-stu-id="1d15e-111">In the [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] Management Console, expand **Certificates (Local Computer)**.</span></span> <span data-ttu-id="1d15e-112">登入的使用者必須具有電腦的管理權限。</span><span class="sxs-lookup"><span data-stu-id="1d15e-112">The logged-in user must have administrative permissions to the computer.</span></span>  
  
4.  <span data-ttu-id="1d15e-113">以滑鼠右鍵按一下**其他人**，指向 **所有工作**，然後按一下 **匯入**。</span><span class="sxs-lookup"><span data-stu-id="1d15e-113">Right-click **Other People**, point to **All Tasks**, and then click **Import**.</span></span>  
  
5.  <span data-ttu-id="1d15e-114">在**憑證匯入精靈歡迎**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="1d15e-114">On the **Certificate Import Wizard Welcome** page, click **Next**.</span></span>  
  
6.  <span data-ttu-id="1d15e-115">在**匯入檔案**頁面上，按一下**瀏覽**並找出包含憑證檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="1d15e-115">On the **File to Import** page, click **Browse** and locate the folder that contains the certificate files.</span></span> <span data-ttu-id="1d15e-116">選取您想要匯入憑證，然後按一下的檔案**開啟**。</span><span class="sxs-lookup"><span data-stu-id="1d15e-116">Select the file from which you want to import the certificate, and then click **Open**.</span></span>  
  
7.  <span data-ttu-id="1d15e-117">在**憑證存放區**頁面上，選取 **自動選取 根據憑證類型的憑證**或**將所有憑證都放入以下的存放區**.</span><span class="sxs-lookup"><span data-stu-id="1d15e-117">On the **Certificate store** page, select either **Automatically select the certificate based on the type of certificate** or **Place all certificates in the following store**.</span></span> <span data-ttu-id="1d15e-118">如果您選取**將所有憑證都放入以下的存放區**，按一下**瀏覽**，選取憑證存放區，按一下**確定**，然後按一下 **下一步**.</span><span class="sxs-lookup"><span data-stu-id="1d15e-118">If you select **Place all certificates in the following store**, click **Browse**, select the certificate store, click **OK**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="1d15e-119">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="1d15e-119">Click **Finish**.</span></span>  
  
### <a name="to-import-a-private-key-certificate"></a><span data-ttu-id="1d15e-120">匯入私密金鑰憑證</span><span class="sxs-lookup"><span data-stu-id="1d15e-120">To import a private-key certificate</span></span>  
  
1.  <span data-ttu-id="1d15e-121">將私密金鑰 (.pfx) 憑證檔案複製到目的伺服器硬碟上的位置。</span><span class="sxs-lookup"><span data-stu-id="1d15e-121">Copy private-key (.pfx) certificate files to a location on the hard disk of the server to which you are copying certificates.</span></span>  
  
2.  <span data-ttu-id="1d15e-122">按一下**啟動**，按一下**執行**，類型**執行身分 /user:\<裝載服務 > mmc**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="1d15e-122">Click **Start**, click **Run**, type **run as /user:\<host service> mmc**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1d15e-123">如\<*裝載服務*>，輸入您在安裝時已自動選取的主機服務的服務名稱[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1d15e-123">For \<*host service*>, type the name of the service that was automatically selected for the host service when you installed [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].</span></span>  
  
3.  <span data-ttu-id="1d15e-124">輸入的密碼\<*裝載服務*>，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="1d15e-124">Type the password for \<*host service*>, and then press **Enter**.</span></span>  
  
4.  <span data-ttu-id="1d15e-125">在[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]管理主控台] 視窗上**檔案**功能表上，按一下 [**新增/移除嵌入式管理單元**。</span><span class="sxs-lookup"><span data-stu-id="1d15e-125">In [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console, on the **File** menu, click **Add/Remove Snap-in**.</span></span>  
  
5.  <span data-ttu-id="1d15e-126">在 [新增/移除嵌入式管理單元] 對話方塊中，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="1d15e-126">In the Add/Remove Snap-in dialog box, click **Add**.</span></span>  
  
6.  <span data-ttu-id="1d15e-127">在 新增獨立嵌入式管理單元 對話方塊中，選取**憑證**，按一下**新增**，按一下 **關閉**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="1d15e-127">In the Add Standalone Snap-in dialog box, select **Certificates**, click **Add**, click **Close**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="1d15e-128">在[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]管理主控台中，展開**憑證-目前使用者**，以滑鼠右鍵按一下**個人**，指向 **所有工作**，然後按一下  **匯入**。</span><span class="sxs-lookup"><span data-stu-id="1d15e-128">In [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console, expand **Certificates - Current User**, right-click **Personal**, point to **All Tasks**, and then click **Import**.</span></span>  
  
8.  <span data-ttu-id="1d15e-129">在**憑證匯入精靈歡迎**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="1d15e-129">On the **Certificate Import Wizard Welcome** page, click **Next**.</span></span>  
  
9. <span data-ttu-id="1d15e-130">在**匯入檔案**頁面上，按一下**瀏覽**並找出包含您要匯入憑證的.pfx 憑證檔案所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="1d15e-130">On the **File to Import** page, click **Browse** and locate the folder that contains the .pfx certificate file that contains the certificate that you want to import.</span></span> <span data-ttu-id="1d15e-131">選取適當的檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="1d15e-131">Select the appropriate file, and then click **Open**.</span></span>  
  
10. <span data-ttu-id="1d15e-132">在**密碼**頁面上，於**密碼**方塊中，輸入私密金鑰檔案的密碼。</span><span class="sxs-lookup"><span data-stu-id="1d15e-132">On the **Password** page, in the **Password** box, type the password for the private-key file.</span></span>  
  
11. <span data-ttu-id="1d15e-133">選取**啟用加強私密金鑰保護**或**標示成可匯出此機碼**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="1d15e-133">Select **Enable strong private key protection** or **Mark this key as exportable**, and then click **Next**.</span></span>  
  
12. <span data-ttu-id="1d15e-134">在**憑證存放區**頁面上，選取 **自動選取 根據憑證類型的憑證**或**將所有憑證都放入以下的存放區**.</span><span class="sxs-lookup"><span data-stu-id="1d15e-134">On the **Certificate store** page, select either **Automatically select the certificate based on the type of certificate** or **Place all certificates in the following store**.</span></span> <span data-ttu-id="1d15e-135">如果您選取**將所有憑證都放入以下的存放區**，按一下**瀏覽**，選取存放區，按一下**確定**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="1d15e-135">If you select **Place all certificates in the following store**, click **Browse**, select the store, click **OK**, and then click **Next**.</span></span>  
  
13. <span data-ttu-id="1d15e-136">在**完成憑證匯入精靈**頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="1d15e-136">On the **Completing the Certificate Import Wizard** page, click **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d15e-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d15e-137">See Also</span></span>  
 <span data-ttu-id="1d15e-138">[設定使用 MMC 匯入的憑證](../../adapters-and-accelerators/accelerator-rosettanet/configuring-certificates-imported-using-mmc.md) </span><span class="sxs-lookup"><span data-stu-id="1d15e-138">[Configuring Certificates Imported Using MMC](../../adapters-and-accelerators/accelerator-rosettanet/configuring-certificates-imported-using-mmc.md) </span></span>  
 [<span data-ttu-id="1d15e-139">CertWizard</span><span class="sxs-lookup"><span data-stu-id="1d15e-139">CertWizard</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/certwizard.md)
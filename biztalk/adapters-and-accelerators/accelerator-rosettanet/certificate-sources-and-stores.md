---
title: 憑證來源與存放區 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- certificates, certificate storage
- importing certificates
- certificates, certificate sources
- certificates, importing
ms.assetid: 3e98fb56-4368-46f3-9329-c44fed11f4fb
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3ade897bb51850b4ef9dd6b530f5fc04c6b2601
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "22210230"
---
# <a name="certificate-sources-and-stores"></a><span data-ttu-id="6367a-102">憑證來源與存放區</span><span class="sxs-lookup"><span data-stu-id="6367a-102">Certificate Sources and Stores</span></span>
<span data-ttu-id="6367a-103">本主題描述從何處匯入憑證，以及在何處存放憑證。</span><span class="sxs-lookup"><span data-stu-id="6367a-103">This topic describes where to import certificates from, and where to store certificates.</span></span>  
  
## <a name="certificate-sources"></a><span data-ttu-id="6367a-104">憑證來源</span><span class="sxs-lookup"><span data-stu-id="6367a-104">Certificate Sources</span></span>  
 <span data-ttu-id="6367a-105">您可以從下列檔案匯入憑證：</span><span class="sxs-lookup"><span data-stu-id="6367a-105">You import certificates from the following files:</span></span>  
  
-   <span data-ttu-id="6367a-106">.pfx 或 .p12 檔案中的私用憑證。</span><span class="sxs-lookup"><span data-stu-id="6367a-106">Private certificates from .pfx or .p12 files.</span></span> <span data-ttu-id="6367a-107">匯入憑證之後，安全地存放這些檔案。</span><span class="sxs-lookup"><span data-stu-id="6367a-107">After importing the certificates, store these files securely.</span></span> <span data-ttu-id="6367a-108">如果您匯入私用的憑證使用 CertWizard 公用程式，您可以設定 **/exportable**切換至`False`，這是預設設定，以便私用憑證無法從存放區匯出到檔案。</span><span class="sxs-lookup"><span data-stu-id="6367a-108">If you import the private certificates using the CertWizard utility, you can set the **/Exportable** switch to `False`, which is the default setting, so that the private certificates cannot be exported from the store into a file.</span></span> <span data-ttu-id="6367a-109">如果您設定 **/exportable**切換至`True`，您可以從憑證檔案匯出這些憑證[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]Management Console (MMC)。</span><span class="sxs-lookup"><span data-stu-id="6367a-109">If you set the **/Exportable** switch to `True`, you can export these certificates to a file from the Certificates [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC).</span></span>  
  
-   <span data-ttu-id="6367a-110">.cer 或 .der 檔案中的公開憑證。</span><span class="sxs-lookup"><span data-stu-id="6367a-110">Public certificates from .cer or .der files.</span></span> <span data-ttu-id="6367a-111">交易夥伴會將憑證放在這些檔案中傳送給您。</span><span class="sxs-lookup"><span data-stu-id="6367a-111">Partners send their certificates to you in these files.</span></span>  
  
-   <span data-ttu-id="6367a-112">.cer 或 .der 檔案中的根憑證。</span><span class="sxs-lookup"><span data-stu-id="6367a-112">Root certificates from .cer or .der files.</span></span> <span data-ttu-id="6367a-113">憑證授權單位會將根憑證放在這些檔案中傳送給您。</span><span class="sxs-lookup"><span data-stu-id="6367a-113">Certification authorities send their root certificates to you in these files.</span></span>  
  
## <a name="certificate-storage"></a><span data-ttu-id="6367a-114">憑證存放區</span><span class="sxs-lookup"><span data-stu-id="6367a-114">Certificate Storage</span></span>  
 <span data-ttu-id="6367a-115">您可以將憑證匯入本機電腦上兩個「憑證」存放區之一。</span><span class="sxs-lookup"><span data-stu-id="6367a-115">You import certificates into one of two Certificates stores on the local computer.</span></span> <span data-ttu-id="6367a-116">您公開憑證存放在**憑證 （本機電腦）** 儲存。</span><span class="sxs-lookup"><span data-stu-id="6367a-116">You store public certificates in the **Certificates (Local Computer)** store.</span></span> <span data-ttu-id="6367a-117">您可以開啟此存放區的節點，開啟**憑證 （本機電腦）** 節點[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] ([!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]) 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="6367a-117">You can open the nodes of this store by opening the **Certificates (Local Computer)** node in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] ([!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]) Management Console.</span></span> <span data-ttu-id="6367a-118">您可以存取**憑證 （本機電腦）** 儲存您的電腦上具有系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="6367a-118">You can access the **Certificates (Local Computer)** store if you have administrative permissions on the computer.</span></span> <span data-ttu-id="6367a-119">將公開憑證存放在下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="6367a-119">Store public certificates in the following folders:</span></span>  
  
-   <span data-ttu-id="6367a-120">主要的個人資料夾中的公開憑證**憑證 （本機電腦）** 儲存</span><span class="sxs-lookup"><span data-stu-id="6367a-120">Home public certificates in the Personal folder in the **Certificates (Local Computer)** store</span></span>  
  
-   <span data-ttu-id="6367a-121">交易夥伴公開憑證中的其他人資料夾**憑證 （本機電腦）** 儲存</span><span class="sxs-lookup"><span data-stu-id="6367a-121">Partner public certificates in the Other People folder of the **Certificates (Local Computer)** store</span></span>  
  
-   <span data-ttu-id="6367a-122">從憑證授權單位的信任根憑證授權單位資料夾中的憑證**憑證 （本機電腦）** 儲存</span><span class="sxs-lookup"><span data-stu-id="6367a-122">Certificates from certification authorities in the Trusted Root Certification Authority folder of the **Certificates (Local Computer)** store</span></span>  
  
 <span data-ttu-id="6367a-123">儲存在私用憑證**憑證-目前使用者**儲存。</span><span class="sxs-lookup"><span data-stu-id="6367a-123">You store private certificates in the **Certificates - Current User** store.</span></span> <span data-ttu-id="6367a-124">您可以開啟此存放區的節點，開啟管理主控台使用**runas**命令與主控件服務帳戶的使用者。</span><span class="sxs-lookup"><span data-stu-id="6367a-124">You can open the nodes of this store by opening the Management Console using the **runas** command with the host service account user.</span></span> <span data-ttu-id="6367a-125">如需詳細資訊，請參閱[匯入憑證](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="6367a-125">For more information, see [Importing Certificates](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6367a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6367a-126">See Also</span></span>  
 <span data-ttu-id="6367a-127">[使用 CertWizard 公用程式匯入憑證](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-the-certwizard-utility.md) </span><span class="sxs-lookup"><span data-stu-id="6367a-127">[Importing Certificates Using the CertWizard Utility](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-the-certwizard-utility.md) </span></span>  
 <span data-ttu-id="6367a-128">[使用 MMC 匯入憑證](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-mmc.md) </span><span class="sxs-lookup"><span data-stu-id="6367a-128">[Importing Certificates Using MMC](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-mmc.md) </span></span>  
 [<span data-ttu-id="6367a-129">匯入憑證&#91;RN3&#93;</span><span class="sxs-lookup"><span data-stu-id="6367a-129">Importing Certificates &#91;RN3&#93;</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/certificate-sources-and-stores.md)
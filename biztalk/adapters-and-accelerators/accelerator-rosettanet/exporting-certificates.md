---
title: "匯出憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exporting certificates
- certificates, exporting
ms.assetid: edeeb300-19d6-44a8-b730-dcd15891cdf9
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32dc7b0f73955c080f875eada2705300800df452
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="exporting-certificates"></a><span data-ttu-id="0e430-102">匯出憑證</span><span class="sxs-lookup"><span data-stu-id="0e430-102">Exporting Certificates</span></span>
<span data-ttu-id="0e430-103">本主題描述如何使用「憑證匯出精靈」來匯出憑證。</span><span class="sxs-lookup"><span data-stu-id="0e430-103">This topic describes how to export a certificate by using the Certificate Export Wizard.</span></span> <span data-ttu-id="0e430-104">使用此精靈可以匯出公開憑證或私用憑證。</span><span class="sxs-lookup"><span data-stu-id="0e430-104">Use this wizard to export either a public certificate or a private certificate.</span></span>  
  
### <a name="to-export-a-partner-certificate"></a><span data-ttu-id="0e430-105">匯出交易夥伴憑證</span><span class="sxs-lookup"><span data-stu-id="0e430-105">To export a partner certificate</span></span>  
  
1.  <span data-ttu-id="0e430-106">按一下**啟動**，指向 **所有程式**，指向 **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] ，然後按一下 [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **管理主控台**.</span><span class="sxs-lookup"><span data-stu-id="0e430-106">Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.</span></span>  
  
2.  <span data-ttu-id="0e430-107">展開**憑證 （本機電腦）**，依序展開**其他人**，然後按一下 **憑證**。</span><span class="sxs-lookup"><span data-stu-id="0e430-107">Expand **Certificates (Local Computer)**, expand **Other People**, and then click **Certificates**.</span></span>  
  
3.  <span data-ttu-id="0e430-108">在右窗格中，以滑鼠右鍵按一下憑證名稱，指向**所有工作**，然後按一下 **匯出**。</span><span class="sxs-lookup"><span data-stu-id="0e430-108">In the right pane, right-click the name of the certificate, point to **All Tasks**, and then click **Export**.</span></span>  
  
4.  <span data-ttu-id="0e430-109">在**歡迎使用 憑證匯出精靈**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0e430-109">On the **Welcome to the Certificate Export Wizard** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="0e430-110">在**匯出檔案格式**頁面上，選取您想要使用之檔案的格式。</span><span class="sxs-lookup"><span data-stu-id="0e430-110">On the **Export File Format** page, select the format that you want to use for the file.</span></span> <span data-ttu-id="0e430-111">此格式通常是 DER 編碼的二進位 x.509 (可匯出二進位編碼的檔案) 或 Base-64 編碼的 x.509 (可匯出 Base-64 編碼的檔案)。</span><span class="sxs-lookup"><span data-stu-id="0e430-111">This format is generally either DER encoded binary x.509 to export a binary-encoded file, or Base-64 encoded x.509 to export a Base-64 encoded file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0e430-112">以 Base-64 將憑證編碼可讓您使用 UNIX 伺服器上的憑證。</span><span class="sxs-lookup"><span data-stu-id="0e430-112">Encoding a certificate in Base-64 lets you use the certificate on a UNIX server.</span></span>  
  
6.  <span data-ttu-id="0e430-113">在**要匯出的檔案**頁面上，按一下**瀏覽**，找出您想要儲存檔案，輸入檔案的名稱，按一下 **下一步**，然後按一下 **完成**.</span><span class="sxs-lookup"><span data-stu-id="0e430-113">On the **File to Export** page, click **Browse**, locate where you want to store the file, type the name of the file, click **Next**, and then click **Finish**.</span></span>  
  
### <a name="to-export-the-home-organization-certificate"></a><span data-ttu-id="0e430-114">匯出主要組織憑證</span><span class="sxs-lookup"><span data-stu-id="0e430-114">To export the home organization certificate</span></span>  
  
1.  <span data-ttu-id="0e430-115">按一下**啟動**，按一下 **執行**，型別**runas /user:\<裝載服務\>mmc**，其中\< *hostservice* \>是您在安裝時，主控件服務關聯的服務名稱[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]，然後按一下 **確定**執行[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]管理主控台 (MMC) 的主控件服務內容中。</span><span class="sxs-lookup"><span data-stu-id="0e430-115">Click **Start**, click **Run**, type **runas /user:\<host service\> mmc**, where \<*hostservice*\> is the name of the service that you associated with the host service when you installed [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)], and then click **OK** to run the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC) in the context of the host service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0e430-116">在您執行**runas**命令，以取得服務主機，其為存取主要組織憑證所需的身份識別。</span><span class="sxs-lookup"><span data-stu-id="0e430-116">You run the **runas** command to assume the identity of the host service, which is required to access the home-organization certificate.</span></span>  
  
2.  <span data-ttu-id="0e430-117">展開**憑證-目前使用者**，依序展開**個人**，然後按一下 **憑證**。</span><span class="sxs-lookup"><span data-stu-id="0e430-117">Expand **Certificates - Current User**, expand **Personal**, and then click **Certificates**.</span></span>  
  
3.  <span data-ttu-id="0e430-118">在右窗格中，以滑鼠右鍵按一下憑證名稱，指向**所有工作**，然後按一下 **匯出**。</span><span class="sxs-lookup"><span data-stu-id="0e430-118">In the right pane, right-click the name of the certificate, point to **All Tasks**, and then click **Export**.</span></span>  
  
4.  <span data-ttu-id="0e430-119">在**歡迎使用 憑證匯出精靈**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0e430-119">On the **Welcome to the Certificate Export Wizard** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="0e430-120">若要匯出憑證的私用的索引鍵相關聯的公開金鑰，將保留**否，不要匯出私密金鑰**選取。</span><span class="sxs-lookup"><span data-stu-id="0e430-120">To export the public key associated with the private key of a certificate, leave **No, do not export the private key** selected.</span></span> <span data-ttu-id="0e430-121">若要匯出的私密金鑰，請選取**是，匯出私密金鑰**。</span><span class="sxs-lookup"><span data-stu-id="0e430-121">To export the private key, select **Yes, export the private key**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0e430-122">如果您選取**是，匯出私密金鑰**，強烈建議您不要傳送產生的檔案給夥伴。</span><span class="sxs-lookup"><span data-stu-id="0e430-122">If you select **Yes, export the private key**, it is highly recommended that you do not send the resulting file to a partner.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0e430-123">**是，匯出私密金鑰**選項將無法使用，如果您未進行私密金鑰可匯出當您第一次匯入。</span><span class="sxs-lookup"><span data-stu-id="0e430-123">The **Yes, export the private key** option will not be available if you did not make the private key exportable when you first imported it.</span></span>  
  
6.  <span data-ttu-id="0e430-124">在**匯出檔案格式**頁面上，選取您想要使用之檔案的格式。</span><span class="sxs-lookup"><span data-stu-id="0e430-124">On the **Export File Format** page, select the format that you want to use for the file.</span></span> <span data-ttu-id="0e430-125">此格式通常是 DER 編碼的二進位 x.509 (可匯出二進位編碼的檔案) 或 Base-64 編碼的 x.509 (可匯出 Base-64 編碼的檔案)。</span><span class="sxs-lookup"><span data-stu-id="0e430-125">This format is generally either DER encoded binary x.509 to export a binary-encoded file, or Base-64 encoded x.509 to export a Base-64 encoded file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0e430-126">以 Base-64 將憑證編碼可讓您使用 UNIX 伺服器上的憑證。</span><span class="sxs-lookup"><span data-stu-id="0e430-126">Encoding a certificate in Base-64 lets you use the certificate on a UNIX server.</span></span>  
  
7.  <span data-ttu-id="0e430-127">在**要匯出的檔案**頁面上，按一下**瀏覽**，找出您想要儲存檔案，輸入檔案的名稱，按一下 **下一步**，然後按一下 **完成**.</span><span class="sxs-lookup"><span data-stu-id="0e430-127">On the **File to Export** page, click **Browse**, locate where you want to store the file, type the name of the file, click **Next**, and then click **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e430-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="0e430-128">See Also</span></span>  
 [<span data-ttu-id="0e430-129">管理憑證</span><span class="sxs-lookup"><span data-stu-id="0e430-129">Managing Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/managing-certificates1.md)
---
title: "部署 Limitations1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: deployment, limitations
ms.assetid: a984ccce-37b2-4738-b652-7232a18e0510
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e65fb1c1a1211865b07c3abb987f0a1d31fbfd69
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deployment-limitations"></a><span data-ttu-id="61c5e-102">部署限制</span><span class="sxs-lookup"><span data-stu-id="61c5e-102">Deployment Limitations</span></span>
<span data-ttu-id="61c5e-103">「 傳輸配接器 」 密碼儲存為顆星 (\*\*\*\*\*\*) 繫結檔案中，會匯出 BizTalk Server 中，並且會傳遞給在同一個管理元件格式。</span><span class="sxs-lookup"><span data-stu-id="61c5e-103">The Transport Adapter password is stored as stars (\*\*\*\*\*\*) in the binding file that is exported by BizTalk Server, and it passes to the management component in the same format.</span></span> <span data-ttu-id="61c5e-104">在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。</span><span class="sxs-lookup"><span data-stu-id="61c5e-104">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="61c5e-105">輸入正確的密碼使用**傳輸屬性**在 BizTalk Server 管理主控台，在匯入繫結檔案之後的頁面。</span><span class="sxs-lookup"><span data-stu-id="61c5e-105">Enter the correct password using the **Transport Properties** page in the BizTalk Server Administration Console after importing the binding file.</span></span>  
  
 <span data-ttu-id="61c5e-106">此為已知的限制狀況。</span><span class="sxs-lookup"><span data-stu-id="61c5e-106">This is a known limitation.</span></span> <span data-ttu-id="61c5e-107">當您匯出繫結資訊時，所產生的繫結檔案不會包含傳輸配接器在接收位置/傳送埠中使用的任何密碼。</span><span class="sxs-lookup"><span data-stu-id="61c5e-107">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="61c5e-108">這可防止密碼資訊以純文字方式出現。</span><span class="sxs-lookup"><span data-stu-id="61c5e-108">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="61c5e-109">下次您使用檔案匯入繫結資訊時，必須使用傳輸屬性頁使用者介面輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="61c5e-109">The next time that you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span> <span data-ttu-id="61c5e-110">或者，您可以在匯入前先暫時修改繫結檔案，方法是將密碼輸入繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="61c5e-110">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="61c5e-111">在這種情況下，您必須在匯入作業順利完成後刪除繫結檔案中的密碼。</span><span class="sxs-lookup"><span data-stu-id="61c5e-111">In this case, you must delete the passwords from the binding file after the import operation successfully finishes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61c5e-112">將包含企業配接器之繫結資訊的 .msi 檔案匯入 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式時，可能會收到匯入錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="61c5e-112">When importing an .msi file in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application containing binding information for any of the Enterprise adapters, you may receive an import error message.</span></span> <span data-ttu-id="61c5e-113">支援的 hotfix 可從 Microsoft 以及在錯誤的完整說明[http://go.microsoft.com/fwlink/?LinkID=196087](http://go.microsoft.com/fwlink/?LinkID=196087)。</span><span class="sxs-lookup"><span data-stu-id="61c5e-113">A supported hotfix is available from Microsoft along with a full description of the error at [http://go.microsoft.com/fwlink/?LinkID=196087](http://go.microsoft.com/fwlink/?LinkID=196087).</span></span>  
  
## <a name="password-limitation-workaround"></a><span data-ttu-id="61c5e-114">密碼限制解決方法</span><span class="sxs-lookup"><span data-stu-id="61c5e-114">Password Limitation Workaround</span></span>  
 <span data-ttu-id="61c5e-115">若要解決這項密碼限制問題，請使用下列其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="61c5e-115">To work around this password limitation, you can use one of the following methods:</span></span>  
  
-   <span data-ttu-id="61c5e-116">在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為純文字。</span><span class="sxs-lookup"><span data-stu-id="61c5e-116">Edit the binding file before importing by replacing the stars with plain text.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="61c5e-117">基於安全理由，並不建議使用這個做法。</span><span class="sxs-lookup"><span data-stu-id="61c5e-117">This is not recommended for security reasons.</span></span>  
  
-   <span data-ttu-id="61c5e-118">在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。</span><span class="sxs-lookup"><span data-stu-id="61c5e-118">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="61c5e-119">輸入正確的密碼使用**傳輸屬性**在 BizTalk Server 管理主控台，在匯入繫結檔案之後的頁面。</span><span class="sxs-lookup"><span data-stu-id="61c5e-119">Enter the correct password using the **Transport Properties** page in the BizTalk Server Administration Console after importing the binding file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61c5e-120">只有當目標電腦上安裝了 Visual Studio，或您開發自訂工具時，才能使用這項解決方法。</span><span class="sxs-lookup"><span data-stu-id="61c5e-120">This work-around can be used only if Visual Studio is installed on the target computer, or if you develop a custom tool.</span></span>  
  
-   <span data-ttu-id="61c5e-121">驗證邏輯系統以及「傳輸」和「接收」服務。</span><span class="sxs-lookup"><span data-stu-id="61c5e-121">Verify the Logical system and the Transmit and Receive services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61c5e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61c5e-122">See Also</span></span>  
 [<span data-ttu-id="61c5e-123">部署連接埠和組件</span><span class="sxs-lookup"><span data-stu-id="61c5e-123">Deploying Ports and Assemblies</span></span>](../core/deploying-ports-and-assemblies2.md)
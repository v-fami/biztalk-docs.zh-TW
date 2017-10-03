---
title: "部署 Limitations4 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- passwords, deployment limitations
- deployment, limitations
ms.assetid: 1312627e-9de2-461e-a8c4-66a9d41bb714
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2d8e33c7274ab0f95c6d7fff1bf9746ac86e420
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deployment-limitations"></a><span data-ttu-id="7fc95-102">部署限制</span><span class="sxs-lookup"><span data-stu-id="7fc95-102">Deployment Limitations</span></span>
<span data-ttu-id="7fc95-103">「傳輸配接器」密碼以星號 (******) 儲存在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 匯出的繫結檔案中，並且會以相同格式傳遞給管理元件。</span><span class="sxs-lookup"><span data-stu-id="7fc95-103">The Transport Adapter password is stored as stars (******) in the binding file that is exported by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and it passes to the management component in the same format.</span></span> <span data-ttu-id="7fc95-104">在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。</span><span class="sxs-lookup"><span data-stu-id="7fc95-104">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span>  
  
 <span data-ttu-id="7fc95-105">當您匯出繫結資訊時，所產生的繫結檔案不會包含傳輸配接器在接收位置/傳送埠中使用的任何密碼。</span><span class="sxs-lookup"><span data-stu-id="7fc95-105">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="7fc95-106">這可防止密碼資訊以純文字方式出現。</span><span class="sxs-lookup"><span data-stu-id="7fc95-106">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="7fc95-107">下次您使用檔案匯入繫結資訊時，必須使用傳輸屬性頁使用者介面輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="7fc95-107">The next time you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span>  
  
 <span data-ttu-id="7fc95-108">或者，您可以在匯入前先暫時修改繫結檔案，方法是將密碼輸入繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="7fc95-108">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="7fc95-109">在這種情況下，您必須在匯入作業順利完成後刪除繫結檔案中的密碼。</span><span class="sxs-lookup"><span data-stu-id="7fc95-109">In this case, you must delete the passwords from the binding file after the import operation successfully completes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7fc95-110">將包含企業配接器之繫結資訊的 .msi 檔案匯入 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式時，可能會收到匯入錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="7fc95-110">When importing an .msi file in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application containing binding information for any of the Enterprise adapters, you may receive an import error message.</span></span> <span data-ttu-id="7fc95-111">支援的 hotfix 可從 Microsoft 以及在錯誤的完整說明[http://go.microsoft.com/fwlink/?LinkId=196087](http://go.microsoft.com/fwlink/?LinkId=196087)。</span><span class="sxs-lookup"><span data-stu-id="7fc95-111">A supported hotfix is available from Microsoft along with a full description of the error at [http://go.microsoft.com/fwlink/?LinkId=196087](http://go.microsoft.com/fwlink/?LinkId=196087).</span></span>  
  
## <a name="password-limitation-workaround"></a><span data-ttu-id="7fc95-112">密碼限制解決方法</span><span class="sxs-lookup"><span data-stu-id="7fc95-112">Password Limitation Workaround</span></span>  
 <span data-ttu-id="7fc95-113">若要解決密碼限制問題，您可以執行下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="7fc95-113">To work around the password limitation, you can do the following.</span></span>  
  
#### <a name="to-work-around-the-password-limitation"></a><span data-ttu-id="7fc95-114">解決密碼限制問題</span><span class="sxs-lookup"><span data-stu-id="7fc95-114">To work around the password limitation</span></span>  
  
1.  <span data-ttu-id="7fc95-115">不使用密碼，改為使用「企業單一登入」。</span><span class="sxs-lookup"><span data-stu-id="7fc95-115">Use Enterprise Single Sign-On instead of using passwords.</span></span> <span data-ttu-id="7fc95-116">使用 SSO 選項只需要先匯入繫結檔案，不需要額外操作。</span><span class="sxs-lookup"><span data-stu-id="7fc95-116">Using the SSO option requires no extra work; only an import of the binding file.</span></span>  
  
2.  <span data-ttu-id="7fc95-117">驗證邏輯系統以及「傳輸」和「接收」服務。</span><span class="sxs-lookup"><span data-stu-id="7fc95-117">Verify the Logical system and the Transmit and Receive services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fc95-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fc95-118">See Also</span></span>  
 [<span data-ttu-id="7fc95-119">部署連接埠和組件</span><span class="sxs-lookup"><span data-stu-id="7fc95-119">Deploying Ports and Assemblies</span></span>](../core/deploying-ports-and-assemblies3.md)
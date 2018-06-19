---
title: 設定輪詢間隔，在批次處理 SQL 配接器接收位置 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- polling interval [receive adapters]
- SQL adapters, polling interval
- receive locations, polling interval
- SQL adapters, receive locations
- receive locations, SQL adapters
ms.assetid: 9053b20d-145a-4445-b414-c0482cf975a0
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 830cafc89c87ce84048bad8f6e4e9f2feb34f565
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269686"
---
# <a name="setting-the-polling-interval-on-the-batching-sql-adapter-receive-location"></a><span data-ttu-id="1a72a-102">在批次處理 SQL 配接器接收位置上設定輪詢間隔</span><span class="sxs-lookup"><span data-stu-id="1a72a-102">Setting the Polling Interval on the Batching SQL Adapter Receive Location</span></span>
<span data-ttu-id="1a72a-103">您可以設定的輪詢間隔上，為批次處理 SQL 配接器接收位置 (**BatchControlMessageRecvLoc**) 以不同的方式開發和生產環境的電腦上。</span><span class="sxs-lookup"><span data-stu-id="1a72a-103">You can set the polling interval on the batching SQL adapter receive location (**BatchControlMessageRecvLoc**) differently on development and production computers.</span></span> <span data-ttu-id="1a72a-104">在程式開發伺服器上，Microsoft 建議您保持預設的 30 秒輪詢間隔，以快速啟動協議的批次處理協調流程。</span><span class="sxs-lookup"><span data-stu-id="1a72a-104">On a development server, Microsoft recommends that you keep the polling interval at the default of 30 seconds, for quick activation of the batching orchestration for an agreement.</span></span> <span data-ttu-id="1a72a-105">然而，在實際執行伺服器上，設定為 30 秒可能會影響效能。</span><span class="sxs-lookup"><span data-stu-id="1a72a-105">However, on a production server, a setting of 30 seconds may affect performance.</span></span> <span data-ttu-id="1a72a-106">一旦批次已啟動，可能需要將輪詢間隔值設高一點，例如 5 分鐘。</span><span class="sxs-lookup"><span data-stu-id="1a72a-106">Once you have activated a batch, you may want to set the polling interval to a higher value, such as five minutes.</span></span>  
  
 <span data-ttu-id="1a72a-107">如需合作對象的詳細資訊，請參閱[管理合作對象](../core/managing-parties.md)。</span><span class="sxs-lookup"><span data-stu-id="1a72a-107">For more information about parties, see [Managing Parties](../core/managing-parties.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1a72a-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="1a72a-108">Prerequisites</span></span>  
 <span data-ttu-id="1a72a-109">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="1a72a-109">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-set-the-polling-interval-on-the-batching-sql-adapter-receive-location"></a><span data-ttu-id="1a72a-110">若要在批次處理 SQL 配接器接收位置上設定輪詢間隔</span><span class="sxs-lookup"><span data-stu-id="1a72a-110">To set the Polling Interval on the Batching SQL Adapter Receive Location</span></span>  
  
1.  <span data-ttu-id="1a72a-111">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下  **BizTalk EDI 應用程式**，然後按一下 **接收位置**。</span><span class="sxs-lookup"><span data-stu-id="1a72a-111">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click **BizTalk EDI Application**, and then click **Receive Locations**.</span></span> <span data-ttu-id="1a72a-112">以滑鼠右鍵按一下**BatchControlMessageRecvLoc**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="1a72a-112">Right-click **BatchControlMessageRecvLoc**, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="1a72a-113">在**接收位置屬性**對話方塊中，於**傳輸**區段中，按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="1a72a-113">In the **Receive Location Properties** dialog box, in the **Transport** section, click **Configure**.</span></span>  
  
3.  <span data-ttu-id="1a72a-114">在**SQL 傳輸屬性**對話方塊方塊中，變更值**輪詢間隔**從預設值為"30"，所要的值。</span><span class="sxs-lookup"><span data-stu-id="1a72a-114">In the **SQL Transport Properties** dialog box, change the value for **Polling Interval** from the default value of "30" to the desired value.</span></span> <span data-ttu-id="1a72a-115">如果是實際執行伺服器，建議值為 "5"。</span><span class="sxs-lookup"><span data-stu-id="1a72a-115">The recommended value for a production server is "5".</span></span>  
  
4.  <span data-ttu-id="1a72a-116">值變更**輪詢的度量單位**的預設值從**秒**至**分鐘**。</span><span class="sxs-lookup"><span data-stu-id="1a72a-116">Change the value of **Polling Unit of Measure** from the default value of **Seconds** to **Minutes**.</span></span>  
  
5.  <span data-ttu-id="1a72a-117">按一下**確定**，然後按一下 **確定**一次</span><span class="sxs-lookup"><span data-stu-id="1a72a-117">Click **OK**, and then click **OK** again</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a72a-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a72a-118">See Also</span></span>  
 [<span data-ttu-id="1a72a-119">管理 EDI 和 AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="1a72a-119">Managing EDI and AS2 Solutions</span></span>](../core/managing-edi-and-as2-solutions.md)
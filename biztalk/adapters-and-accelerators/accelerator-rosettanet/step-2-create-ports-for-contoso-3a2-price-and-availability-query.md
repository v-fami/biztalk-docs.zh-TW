---
title: 步驟 2： 建立 Contoso 3A2 價格與可用性查詢回應案例中使用 BizTalk 總管 中的連接埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- private process tutorial, creating ports
ms.assetid: e0b12a96-e799-47ac-8293-7de10662bdf0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64101a31b1d1ea9c7af00471c5d764a1d8cfe598
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-creating-ports-for-the-contoso-3a2-price-and-availability-queryresponse-scenario"></a><span data-ttu-id="b8c01-102">步驟 2： 為 Contoso 3A2 價格與可用性查詢/回應實例建立連接埠</span><span class="sxs-lookup"><span data-stu-id="b8c01-102">Step 2: Creating Ports for the Contoso 3A2 Price and Availability Query/Response Scenario</span></span>
<span data-ttu-id="b8c01-103">在此步驟中，您可以建立使用由 BizTalk Server 所提供的 SQL 配接器的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="b8c01-103">In this step, you create send ports using the SQL adapter provided by BizTalk Server.</span></span> <span data-ttu-id="b8c01-104">您可以使用 SQL 連接埠傳送並接收往返於 Contoso ERP 系統的「3A2 價格與可用性」回應。</span><span class="sxs-lookup"><span data-stu-id="b8c01-104">You use the SQL port for sending and receiving the 3A2 Price and Availability response to and from the ERP system for Contoso.</span></span>  
  
### <a name="to-configure-a-send-port-using-the-sql-adapter"></a><span data-ttu-id="b8c01-105">使用 SQL 配接器設定傳送埠</span><span class="sxs-lookup"><span data-stu-id="b8c01-105">To configure a send port using the SQL adapter</span></span>  
  
1.  <span data-ttu-id="b8c01-106">在 Visual Studio 中，在**檢視**功能表上，按一下  **BizTalk 總管**。</span><span class="sxs-lookup"><span data-stu-id="b8c01-106">In Visual Studio, on the **View** menu, click **BizTalk Explorer**.</span></span>  
  
2.  <span data-ttu-id="b8c01-107">在 BizTalk 總管 中，以滑鼠右鍵按一下**傳送埠**，然後按一下 **新增傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="b8c01-107">In BizTalk Explorer, right-click **Send Ports**, and then click **Add Send Port**.</span></span>  
  
3.  <span data-ttu-id="b8c01-108">在 [建立新傳送埠] 對話方塊中，選取**靜態請求-回應連接埠**從下拉式清單，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="b8c01-108">In the Create New Send Port dialog box, select **Static Solicit-Response Port** from the drop-down list, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="b8c01-109">在 [靜態請求-回應傳送埠屬性] 對話方塊中**名稱**方塊中，輸入**3A2SQLReqResponseSendPort**。</span><span class="sxs-lookup"><span data-stu-id="b8c01-109">In the Static Solicit-Response Send Port Properties dialog box, in the **Name** box, type **3A2SQLReqResponseSendPort**.</span></span>  
  
5.  <span data-ttu-id="b8c01-110">在 [屬性] 視窗中**一般**標題之下，選取**SQL**為**傳輸類型**。</span><span class="sxs-lookup"><span data-stu-id="b8c01-110">In the Properties window under the **General** heading, select **SQL** as the **Transport Type**.</span></span>  
  
6.  <span data-ttu-id="b8c01-111">在**位址 URI**方塊中，按一下省略符號按鈕 (**...**).</span><span class="sxs-lookup"><span data-stu-id="b8c01-111">In the **Address URI** box, click the ellipsis button (**…**).</span></span>  
  
7.  <span data-ttu-id="b8c01-112">在 [SQL 傳輸屬性] 對話方塊中，按一下省略符號按鈕 (**...**) 旁邊**連接字串**方塊。</span><span class="sxs-lookup"><span data-stu-id="b8c01-112">In the SQL Transport Properties dialog box, click the ellipsis button (**…**) next to the **Connection String** box.</span></span>  
  
8.  <span data-ttu-id="b8c01-113">在 [資料連結屬性] 對話方塊中**選取或輸入伺服器名稱**方塊中，輸入**localhost**。</span><span class="sxs-lookup"><span data-stu-id="b8c01-113">In the Data Link Properties dialog box, in the **Select or enter a server name** box, type **localhost**.</span></span>  
  
9. <span data-ttu-id="b8c01-114">選取**使用 Windows NT 整合式安全性**。</span><span class="sxs-lookup"><span data-stu-id="b8c01-114">Select **Use Windows NT Integrated security**.</span></span>  
  
10. <span data-ttu-id="b8c01-115">在**選取的資料庫伺服器上**方塊中，選取**Contoso**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="b8c01-115">In the **Select the database on the server** box, select **Contoso**, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="b8c01-116">在 [SQL 傳輸屬性] 對話方塊中**文件目標命名空間**方塊中，輸入**http://Contoso.com/Price**。</span><span class="sxs-lookup"><span data-stu-id="b8c01-116">In the SQL Transport Properties dialog box, in the **Document Target Namespace** box, type **http://Contoso.com/Price**.</span></span>  
  
12. <span data-ttu-id="b8c01-117">在**回應文件根項目名稱**方塊中，輸入**rootPriceResponse**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="b8c01-117">In the **Response Document Root Element Name** box, type **rootPriceResponse**, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="b8c01-118">在 靜態請求-回應傳送埠屬性 對話方塊的左窗格中，按一下 **傳送**。</span><span class="sxs-lookup"><span data-stu-id="b8c01-118">In the left pane of the Static Solicit-Response Send Port Properties dialog box, click **Send**.</span></span>  
  
14. <span data-ttu-id="b8c01-119">在 [靜態請求-回應傳送埠屬性-組態-傳送-一般] 對話方塊中**傳送管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="b8c01-119">In the Static Solicit-Response Send Port Properties-Configurations-Send-General dialog box, in the **Send Pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
15. <span data-ttu-id="b8c01-120">在**接收管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.XMLReceive**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="b8c01-120">In the **Receive Pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.XMLReceive**, and then click **OK**.</span></span>  
  
16. <span data-ttu-id="b8c01-121">在 BizTalk 總管 中，以滑鼠右鍵按一下**3A2SQLReqResponseSendPort**，然後按一下 **登錄**。</span><span class="sxs-lookup"><span data-stu-id="b8c01-121">In BizTalk Explorer, right-click **3A2SQLReqResponseSendPort**, and then click **Enlist**.</span></span> <span data-ttu-id="b8c01-122">以滑鼠右鍵按一下它，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="b8c01-122">Right-click it again, and click **Start**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8c01-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8c01-123">See Also</span></span>  
 [<span data-ttu-id="b8c01-124">建立與修改 Contoso 私用程序</span><span class="sxs-lookup"><span data-stu-id="b8c01-124">Creating and Modifying the Private Process for Contoso</span></span>](creating-and-modifying-the-private-process-for-contoso.md)
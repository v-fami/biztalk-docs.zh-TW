---
title: 在 PeopleSoft 中產生 XML 或結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- generating schemas
- schemas, generating
- generating XML
- XML, generating
ms.assetid: adfe2936-0dc2-42d2-b26a-718f8cc57eff
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fadd89a1e929d672f1b2c8839248d5d03cb27d1c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005631"
---
# <a name="generating-xml-or-schema-in-peoplesoft"></a><span data-ttu-id="9368a-102">在 PeopleSoft 中產生 XML 或結構描述</span><span class="sxs-lookup"><span data-stu-id="9368a-102">Generating XML or Schema in PeopleSoft</span></span>
<span data-ttu-id="9368a-103">下列程序說明如何使用 PeopleSoft Enterprise 建立 XML 檔案及觸發 PeopleSoft 事件。</span><span class="sxs-lookup"><span data-stu-id="9368a-103">The following procedure describes how to use PeopleSoft Enterprise to create an XML file and trigger a PeopleSoft event.</span></span> <span data-ttu-id="9368a-104">若要執行此動作，您會在 PeopleSoft 環境中進行一些變更。</span><span class="sxs-lookup"><span data-stu-id="9368a-104">To do this, you change something in the PeopleSoft environment.</span></span> <span data-ttu-id="9368a-105">此變更會啟動 XML 檔案，該檔案會傳送至您在協調流程中設定要監視的檔案資料夾。</span><span class="sxs-lookup"><span data-stu-id="9368a-105">The change activates an XML file, which is sent to the file folder that you set in your orchestration to be monitored.</span></span> <span data-ttu-id="9368a-106">稍後，您會在 BizTalk Server 中匯入該 XML 並產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="9368a-106">Later, in BizTalk Server, you import the XML and generate a schema.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9368a-107">當您建立 Location 與 MSEXTERNAL 節點的關聯時，對 Location Value 所做的任何變更都會產生 XML 文件，並觸發事件。</span><span class="sxs-lookup"><span data-stu-id="9368a-107">When you associate the Location with the MSEXTERNAL node, any change made to Location Value generates an XML document—triggering an event.</span></span> <span data-ttu-id="9368a-108">登錄並啟動協調流程之後，您可以瀏覽 PeopleSoft 畫面到 LOCATION 畫面。</span><span class="sxs-lookup"><span data-stu-id="9368a-108">After enlisting and starting your orchestration, you can navigate through the PeopleSoft screens to the LOCATION screen.</span></span> <span data-ttu-id="9368a-109">若變更 Location Value 並儲存變更，\out 目錄中便會出現對應的 XML。</span><span class="sxs-lookup"><span data-stu-id="9368a-109">If you make a change to Location Value and save your change, a corresponding XML appears in your \out directory.</span></span>  
  
### <a name="to-generate-xml-or-schema-in-peoplesoft"></a><span data-ttu-id="9368a-110">在 PeopleSoft 中產生 XML 或結構描述</span><span class="sxs-lookup"><span data-stu-id="9368a-110">To generate XML or Schema in PeopleSoft</span></span>  
  
1. <span data-ttu-id="9368a-111">在 PeopleSoft 應用程式中，指向**Set up Financials**，指向**Supply Chain**，指向**一般定義**，指向 **位置**，然後選取**位置**。</span><span class="sxs-lookup"><span data-stu-id="9368a-111">In the PeopleSoft application, point to **Set up Financials**, point to **Supply Chain**, point to **Common Definitions**, point to **Location**, and then select **Location**.</span></span>  
  
2. <span data-ttu-id="9368a-112">在 **位置**畫面上，輸入下列資訊：</span><span class="sxs-lookup"><span data-stu-id="9368a-112">On the **Location** screen, enter the following information:</span></span>  
  
   - <span data-ttu-id="9368a-113">**集合識別碼：** 輸入**共用**。</span><span class="sxs-lookup"><span data-stu-id="9368a-113">**Set ID:** Enter **SHARE**.</span></span>  
  
   - <span data-ttu-id="9368a-114">**Location Code:** 輸入開頭的程式碼`WKLOC`。</span><span class="sxs-lookup"><span data-stu-id="9368a-114">**Location Code:** Enter a code that starts with `WKLOC`.</span></span>  
  
     <span data-ttu-id="9368a-115">![](../core/media/psadapter-18-task-sharesearch.gif "PSAdapter_18_Task_ShareSearch")</span><span class="sxs-lookup"><span data-stu-id="9368a-115">![](../core/media/psadapter-18-task-sharesearch.gif "PSAdapter_18_Task_ShareSearch")</span></span>  
  
3. <span data-ttu-id="9368a-116">按一下 **搜尋**，然後按一下**Correct History**將畫面置於**編輯**模式。</span><span class="sxs-lookup"><span data-stu-id="9368a-116">Click **Search**, and then click **Correct History** to put the screen in **Edit** mode.</span></span>  
  
    <span data-ttu-id="9368a-117">![](../core/media/psadapter-19-task-correcthistory.gif "PSAdapter_19_Task_CorrectHistory")</span><span class="sxs-lookup"><span data-stu-id="9368a-117">![](../core/media/psadapter-19-task-correcthistory.gif "PSAdapter_19_Task_CorrectHistory")</span></span>  
  
4. <span data-ttu-id="9368a-118">在畫面上，欄位進行變更，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="9368a-118">Make a change to a field on the screen, and then click **Save**.</span></span>  
  
5. <span data-ttu-id="9368a-119">指向**PeopleTools**，指向**Integration Broker**，指向**監視器**，然後選取**Monitor Message**。</span><span class="sxs-lookup"><span data-stu-id="9368a-119">Point to **PeopleTools**, point to **Integration Broker**, point to **Monitor**, and then select **Monitor Message**.</span></span>  
  
    <span data-ttu-id="9368a-120">![](../core/media/psadapter-20-task-monitormessage.gif "PSAdapter_20_Task_MonitorMessage")</span><span class="sxs-lookup"><span data-stu-id="9368a-120">![](../core/media/psadapter-20-task-monitormessage.gif "PSAdapter_20_Task_MonitorMessage")</span></span>  
  
6. <span data-ttu-id="9368a-121">請確定**通道型別**是**訊息執行個體**，然後按一下**重新整理**。</span><span class="sxs-lookup"><span data-stu-id="9368a-121">Make sure that **Channel Type** is **Message Instance**, and then click **Refresh**.</span></span>  
  
7. <span data-ttu-id="9368a-122">在 [**完成**] 欄中，按一下此數字。</span><span class="sxs-lookup"><span data-stu-id="9368a-122">In the **Done** column, click the number.</span></span>  
  
8. <span data-ttu-id="9368a-123">捲動到清單底部，按一下**詳細資料**連結**LOCATION_SYNC**訊息。</span><span class="sxs-lookup"><span data-stu-id="9368a-123">Scroll to the bottom of the list and click the **Details** link on a **LOCATION_SYNC** message.</span></span>  
  
    <span data-ttu-id="9368a-124">![](../core/media/psadapter-21-task-detailslink.gif "PSAdapter_21_Task_DetailsLink")</span><span class="sxs-lookup"><span data-stu-id="9368a-124">![](../core/media/psadapter-21-task-detailslink.gif "PSAdapter_21_Task_DetailsLink")</span></span>  
  
9. <span data-ttu-id="9368a-125">按一下 **檢視 XML**上**MSEXTERNAL**節點。</span><span class="sxs-lookup"><span data-stu-id="9368a-125">Click **View XML** on a **MSEXTERNAL** Node.</span></span>  
  
     <span data-ttu-id="9368a-126">![](../core/media/psadapter-22-task-viewxml.gif "PSAdapter_22_Task_ViewXML")</span><span class="sxs-lookup"><span data-stu-id="9368a-126">![](../core/media/psadapter-22-task-viewxml.gif "PSAdapter_22_Task_ViewXML")</span></span>  
  
     <span data-ttu-id="9368a-127">將 XML 內容複製並貼到您的 BizTalk Server 專案可以存取的檔案中。</span><span class="sxs-lookup"><span data-stu-id="9368a-127">Copy and paste the contents of the XML into a file that can be accessed by your BizTalk Server project.</span></span>  
  
     <span data-ttu-id="9368a-128">![](../core/media/psadapter-23-task-xmlresult.gif "PSAdapter_23_Task_XMLResult")</span><span class="sxs-lookup"><span data-stu-id="9368a-128">![](../core/media/psadapter-23-task-xmlresult.gif "PSAdapter_23_Task_XMLResult")</span></span>  
  
10. <span data-ttu-id="9368a-129">記住此檔案的位置，您會在 BizTalk Server 中加以參考。</span><span class="sxs-lookup"><span data-stu-id="9368a-129">Remember the location of the file;  you reference it in BizTalk Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9368a-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9368a-130">See Also</span></span>  
 [<span data-ttu-id="9368a-131">附錄 B：使用 PeopleSoft 應用程式</span><span class="sxs-lookup"><span data-stu-id="9368a-131">Appendix B: Using the PeopleSoft Application</span></span>](../core/appendix-b-using-the-peoplesoft-application.md)
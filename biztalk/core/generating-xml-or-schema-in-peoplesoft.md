---
title: "在 PeopleSoft 中產生 XML 或結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generating schemas
- schemas, generating
- generating XML
- XML, generating
ms.assetid: adfe2936-0dc2-42d2-b26a-718f8cc57eff
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a7fbd164f7c0d380f6ee0c0fda59098203f7585
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="generating-xml-or-schema-in-peoplesoft"></a><span data-ttu-id="fe3de-102">在 PeopleSoft 中產生 XML 或結構描述</span><span class="sxs-lookup"><span data-stu-id="fe3de-102">Generating XML or Schema in PeopleSoft</span></span>
<span data-ttu-id="fe3de-103">下列程序說明如何使用 PeopleSoft Enterprise 建立 XML 檔案及觸發 PeopleSoft 事件。</span><span class="sxs-lookup"><span data-stu-id="fe3de-103">The following procedure describes how to use PeopleSoft Enterprise to create an XML file and trigger a PeopleSoft event.</span></span> <span data-ttu-id="fe3de-104">若要執行此動作，您會在 PeopleSoft 環境中進行一些變更。</span><span class="sxs-lookup"><span data-stu-id="fe3de-104">To do this, you change something in the PeopleSoft environment.</span></span> <span data-ttu-id="fe3de-105">此變更會啟動 XML 檔案，該檔案會傳送至您在協調流程中設定要監視的檔案資料夾。</span><span class="sxs-lookup"><span data-stu-id="fe3de-105">The change activates an XML file, which is sent to the file folder that you set in your orchestration to be monitored.</span></span> <span data-ttu-id="fe3de-106">稍後，您會在 BizTalk Server 中匯入該 XML 並產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="fe3de-106">Later, in BizTalk Server, you import the XML and generate a schema.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe3de-107">當您建立 Location 與 MSEXTERNAL 節點的關聯時，對 Location Value 所做的任何變更都會產生 XML 文件，並觸發事件。</span><span class="sxs-lookup"><span data-stu-id="fe3de-107">When you associate the Location with the MSEXTERNAL node, any change made to Location Value generates an XML document—triggering an event.</span></span> <span data-ttu-id="fe3de-108">登錄並啟動協調流程之後，您可以瀏覽 PeopleSoft 畫面到 LOCATION 畫面。</span><span class="sxs-lookup"><span data-stu-id="fe3de-108">After enlisting and starting your orchestration, you can navigate through the PeopleSoft screens to the LOCATION screen.</span></span> <span data-ttu-id="fe3de-109">若變更 Location Value 並儲存變更，\out 目錄中便會出現對應的 XML。</span><span class="sxs-lookup"><span data-stu-id="fe3de-109">If you make a change to Location Value and save your change, a corresponding XML appears in your \out directory.</span></span>  
  
### <a name="to-generate-xml-or-schema-in-peoplesoft"></a><span data-ttu-id="fe3de-110">在 PeopleSoft 中產生 XML 或結構描述</span><span class="sxs-lookup"><span data-stu-id="fe3de-110">To generate XML or Schema in PeopleSoft</span></span>  
  
1.  <span data-ttu-id="fe3de-111">在 PeopleSoft 應用程式中，指向**Set up Financials**，指向**供應鏈**，指向 **一般定義**，指向 **位置**，然後選取**位置**。</span><span class="sxs-lookup"><span data-stu-id="fe3de-111">In the PeopleSoft application, point to **Set up Financials**, point to **Supply Chain**, point to **Common Definitions**, point to **Location**, and then select **Location**.</span></span>  
  
2.  <span data-ttu-id="fe3de-112">在**位置**畫面上，輸入下列資訊：</span><span class="sxs-lookup"><span data-stu-id="fe3de-112">On the **Location** screen, enter the following information:</span></span>  
  
    -   <span data-ttu-id="fe3de-113">**Set ID:**輸入**共用**。</span><span class="sxs-lookup"><span data-stu-id="fe3de-113">**Set ID:** Enter **SHARE**.</span></span>  
  
    -   <span data-ttu-id="fe3de-114">**Location Code:**輸入開頭的程式碼`WKLOC`。</span><span class="sxs-lookup"><span data-stu-id="fe3de-114">**Location Code:** Enter a code that starts with `WKLOC`.</span></span>  
  
     ![](../core/media/psadapter-18-task-sharesearch.gif "PSAdapter_18_Task_ShareSearch")  
  
3.  <span data-ttu-id="fe3de-115">按一下**搜尋**，然後按一下  **Correct History**將畫面置於**編輯**模式。</span><span class="sxs-lookup"><span data-stu-id="fe3de-115">Click **Search**, and then click **Correct History** to put the screen in **Edit** mode.</span></span>  
  
     ![](../core/media/psadapter-19-task-correcthistory.gif "PSAdapter_19_Task_CorrectHistory")  
  
4.  <span data-ttu-id="fe3de-116">在畫面上，欄位進行變更，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="fe3de-116">Make a change to a field on the screen, and then click **Save**.</span></span>  
  
5.  <span data-ttu-id="fe3de-117">指向**PeopleTools**，指向  **Integration Broker**，指向 **監視器**，然後選取**Monitor Message**。</span><span class="sxs-lookup"><span data-stu-id="fe3de-117">Point to **PeopleTools**, point to **Integration Broker**, point to **Monitor**, and then select **Monitor Message**.</span></span>  
  
     ![](../core/media/psadapter-20-task-monitormessage.gif "PSAdapter_20_Task_MonitorMessage")  
  
6.  <span data-ttu-id="fe3de-118">請確定**通道型別**是**訊息執行個體**，然後按一下 **重新整理**。</span><span class="sxs-lookup"><span data-stu-id="fe3de-118">Make sure that **Channel Type** is **Message Instance**, and then click **Refresh**.</span></span>  
  
7.  <span data-ttu-id="fe3de-119">在**完成**資料行中，按一下的數字。</span><span class="sxs-lookup"><span data-stu-id="fe3de-119">In the **Done** column, click the number.</span></span>  
  
8.  <span data-ttu-id="fe3de-120">捲動到清單底部，按一下**詳細資料**連結**LOCATION_SYNC**訊息。</span><span class="sxs-lookup"><span data-stu-id="fe3de-120">Scroll to the bottom of the list and click the **Details** link on a **LOCATION_SYNC** message.</span></span>  
  
     ![](../core/media/psadapter-21-task-detailslink.gif "PSAdapter_21_Task_DetailsLink")  
  
9. <span data-ttu-id="fe3de-121">按一下**檢視 XML**上**MSEXTERNAL**節點。</span><span class="sxs-lookup"><span data-stu-id="fe3de-121">Click **View XML** on a **MSEXTERNAL** Node.</span></span>  
  
     ![](../core/media/psadapter-22-task-viewxml.gif "PSAdapter_22_Task_ViewXML")  
  
     <span data-ttu-id="fe3de-122">將 XML 內容複製並貼到您的 BizTalk Server 專案可以存取的檔案中。</span><span class="sxs-lookup"><span data-stu-id="fe3de-122">Copy and paste the contents of the XML into a file that can be accessed by your BizTalk Server project.</span></span>  
  
     ![](../core/media/psadapter-23-task-xmlresult.gif "PSAdapter_23_Task_XMLResult")  
  
10. <span data-ttu-id="fe3de-123">記住此檔案的位置，您會在 BizTalk Server 中加以參考。</span><span class="sxs-lookup"><span data-stu-id="fe3de-123">Remember the location of the file;  you reference it in BizTalk Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe3de-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe3de-124">See Also</span></span>  
 [<span data-ttu-id="fe3de-125">附錄 b： 使用 PeopleSoft 應用程式</span><span class="sxs-lookup"><span data-stu-id="fe3de-125">Appendix B: Using the PeopleSoft Application</span></span>](../core/appendix-b-using-the-peoplesoft-application.md)
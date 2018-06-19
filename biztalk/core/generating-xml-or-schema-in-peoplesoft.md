---
title: 在 PeopleSoft 中產生 XML 或結構描述 |Microsoft 文件
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
ms.openlocfilehash: 1a7fbd164f7c0d380f6ee0c0fda59098203f7585
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246686"
---
# <a name="generating-xml-or-schema-in-peoplesoft"></a>在 PeopleSoft 中產生 XML 或結構描述
下列程序說明如何使用 PeopleSoft Enterprise 建立 XML 檔案及觸發 PeopleSoft 事件。 若要執行此動作，您會在 PeopleSoft 環境中進行一些變更。 此變更會啟動 XML 檔案，該檔案會傳送至您在協調流程中設定要監視的檔案資料夾。 稍後，您會在 BizTalk Server 中匯入該 XML 並產生結構描述。  
  
> [!NOTE]
>  當您建立 Location 與 MSEXTERNAL 節點的關聯時，對 Location Value 所做的任何變更都會產生 XML 文件，並觸發事件。 登錄並啟動協調流程之後，您可以瀏覽 PeopleSoft 畫面到 LOCATION 畫面。 若變更 Location Value 並儲存變更，\out 目錄中便會出現對應的 XML。  
  
### <a name="to-generate-xml-or-schema-in-peoplesoft"></a>在 PeopleSoft 中產生 XML 或結構描述  
  
1.  在 PeopleSoft 應用程式中，指向**Set up Financials**，指向**供應鏈**，指向 **一般定義**，指向 **位置**，然後選取**位置**。  
  
2.  在**位置**畫面上，輸入下列資訊：  
  
    -   **Set ID:** 輸入**共用**。  
  
    -   **Location Code:** 輸入開頭的程式碼`WKLOC`。  
  
     ![](../core/media/psadapter-18-task-sharesearch.gif "PSAdapter_18_Task_ShareSearch")  
  
3.  按一下**搜尋**，然後按一下  **Correct History**將畫面置於**編輯**模式。  
  
     ![](../core/media/psadapter-19-task-correcthistory.gif "PSAdapter_19_Task_CorrectHistory")  
  
4.  在畫面上，欄位進行變更，然後按一下 **儲存**。  
  
5.  指向**PeopleTools**，指向  **Integration Broker**，指向 **監視器**，然後選取**Monitor Message**。  
  
     ![](../core/media/psadapter-20-task-monitormessage.gif "PSAdapter_20_Task_MonitorMessage")  
  
6.  請確定**通道型別**是**訊息執行個體**，然後按一下 **重新整理**。  
  
7.  在**完成**資料行中，按一下的數字。  
  
8.  捲動到清單底部，按一下**詳細資料**連結**LOCATION_SYNC**訊息。  
  
     ![](../core/media/psadapter-21-task-detailslink.gif "PSAdapter_21_Task_DetailsLink")  
  
9. 按一下**檢視 XML**上**MSEXTERNAL**節點。  
  
     ![](../core/media/psadapter-22-task-viewxml.gif "PSAdapter_22_Task_ViewXML")  
  
     將 XML 內容複製並貼到您的 BizTalk Server 專案可以存取的檔案中。  
  
     ![](../core/media/psadapter-23-task-xmlresult.gif "PSAdapter_23_Task_XMLResult")  
  
10. 記住此檔案的位置，您會在 BizTalk Server 中加以參考。  
  
## <a name="see-also"></a>另請參閱  
 [附錄 b： 使用 PeopleSoft 應用程式](../core/appendix-b-using-the-peoplesoft-application.md)
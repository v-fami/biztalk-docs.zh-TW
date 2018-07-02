---
title: 步驟 2： 建立庫存要求結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0fa9ad9f-b815-4baf-8299-556869b8dde7
caps.latest.revision: 45
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4c434fe058380f7c9384e3e6c7308393ec01be0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985759"
---
# <a name="step-2-create-the-inventory-request-schema"></a>步驟 2：建立庫存要求結構描述
![步驟 5 之 2](../core/media/step-2of5.gif "Step_2of5")  

 **若要完成的時間：** 7 分鐘  

 **目標：** 在此步驟中，您會定義庫存補充訊息的結構描述。  倉儲系統會傳送這個訊息，以便要求庫存補充。  這是您必須針對此專案建立的其中一個結構描述。  

 **用途：** XML 不僅會結構化和識別資訊與標準化的標記程式碼，但它也能夠使用結構描述。 結構描述是一種 XML 文件，其運作方式就如同字典，而且會由其他 XML 文件當做參考使用。 結構描述程式碼會定義 XML 項目的拼字以及這些項目所包含的資料類型。 使用結構描述可讓程式輕易地處理 XML 文件並確保資訊的結構和類型正確無誤。  

## <a name="prerequisites"></a>必要條件  
 開始此步驟之前，請注意下列需求：  

-   在開始此步驟之前必須先完成[步驟 1： 建立 EAISchemas 專案](../core/step-1-create-eaischemas-project.md)。  

## <a name="procedures"></a>程序  
 在 [步驟 1： 建立 EAISchemas 專案](../core/step-1-create-eaischemas-project.md)，您建立了新[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]專案。  如果您關閉了 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 視窗，就可以使用下列程序來開啟專案。  否則，您可以略過這個程序：「若要開啟 Visual Studio 專案」。  

#### <a name="to-open-the-visual-studio-project"></a>若要開啟 Visual Studio 專案  

1. 開始**Microsoft Visual Studio**。  

2. 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**開啟**，然後按一下 **專案/方案**。  

3. 在 [**開啟專案**] 對話方塊中，瀏覽至**C:\BTSTutorials\EAISolution\EAISolution.sln**方案檔案，然後按一下**開啟**。  

   在下列程序中，您會將新的結構描述檔案新增至庫存補充訊息的專案。  

#### <a name="to-add-a-new-schema-to-the-project"></a>新增新結構描述至專案  

1. 在 [方案總管] 中，以滑鼠右鍵按一下**EAISchemas**專案，指向**新增**，然後按一下**新項目**。  

2. 在 **加入新項目-EAISchemas**對話方塊方塊中，執行下列動作：  


   |        使用         |                   以進行此動作                   |
   |-------------------------|------------------------------------------------|
   | **已安裝的範本** | 按一下 **結構描述檔案**，然後按一下**結構描述**。 |
   |        **名稱**         |             型別**Request.xsd**。              |


3. 按一下 **[加入]**。 會出現結構描述樹狀結構與 [XSD] 窗格。 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的這個區域稱為「BizTalk 編輯器」。 此外，新結構描述在 [方案總管] 中會顯示於 EAISchemas 專案下方。  

    ![BizTalk 專案的不同部分](../core/media/differentpartsofbiztalkserver.gif "DifferentpartsofBizTalkServer")  

#### <a name="to-add-elements-to-the-schema"></a>若要將項目新增至結構描述  

1. 在 結構描述樹狀目錄中，按一下**根**節點。  

2. 在 [屬性] 窗格中，將變更的值**節點名稱**屬性設`Request`，然後按 ENTER 鍵。  

3. 在結構描述樹狀目錄中，以滑鼠右鍵按一下**要求**節點，指向**插入結構描述節點**，然後按一下**子記錄**。  

4. 型別`Header`做為子記錄，然後按 ENTER 鍵的新名稱。  

5. 重複步驟 3 和 4，以建立第二個子記錄**要求**節點，並將它命名`Items`。  

6. 在結構描述樹狀目錄中，以滑鼠右鍵按一下**標頭**節點，指向**插入結構描述節點**，然後按一下**子欄位項目**。  

7. 型別`ReqID`做為項目，然後按 ENTER 鍵新名稱。  

8. 重複步驟 6 和 7，以建立第二個子欄位項目，如**標頭**節點，並將它命名`OrderDate`。

9. 重複步驟 6 和 7，以建立第三個子欄位項目，如**標頭**節點，並將它命名`GrandTotal`。

10. 在結構描述樹狀目錄中，以滑鼠右鍵按一下**項目**節點，指向**插入結構描述節點**，然後按一下**子記錄**。  

11. 型別`Item`做為子記錄，然後按 ENTER 鍵的新名稱。  

12. 在結構描述樹狀目錄中，以滑鼠右鍵按一下**項目** 節點，並新增下列子欄位項目：  

    - `Description`  

    - `Quantity`  

    - `UnitPrice`  

      已完成的 Request.xsd 看起來應該如下圖所示。  

      ![具有要求結構描述的方案總管](../core/media/solutionexplorerwiththerequestschema.gif "SolutionExplorerwiththeRequestSchema")  

    當您將節點新增至結構描述時，BizTalk 編輯器就會針對其屬性提供一組預設值。  您必須根據需求設定這些屬性。  

#### <a name="to-configure-the-elements"></a>若要設定項目  

1. 在 結構描述樹狀目錄中，按一下**OrderDate**來選取它。  

2. 在 [屬性] 窗格中，變更**資料型別**要**xs: datetime**。  

3. 重複步驟 1 和 2 來設定下列屬性：  

   |元素|屬性|ReplTest1|  
   |-------------|--------------|-----------|  
   |**GrandTotal**|**資料類型**|**Xs: decimal**|  
   |**項目**|**Max Occurs**|**未繫結**|  
   |**項目**|**Min Occurs**|**1**|  
   |**數量**|**資料類型**|**xs:unsignedInt**|  

   雖然一個結構描述可以具有許多項目，不過您的應用程式可能只需要您使用其中少數項目進行資料處理。 為了節省電腦資源，BizTalk Server 不會自動讀取每個結構描述項目。 如果您想要讓 BizTalk Server 讀取特定項目的資料，就必須使用 BizTalk 編輯器來升級該項目的屬性，以便識別該項目。  

   我們將在建立協調流程[第 2 課： 定義商務程序](../core/lesson-2-define-the-business-process.md)將根據 GrandTotal 欄位來路由傳送訊息。  因此，我們必須升級 GrandTotal 欄位。  

#### <a name="to-promote-an-element"></a>若要升級項目  

1.  在結構描述樹狀目錄中，以滑鼠右鍵按一下**GrandTotal**，指向**升階**，然後按一下**快速升級**。  

2.  按一下 **確定**確認新增屬性結構描述。  

3.  按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。  

## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在這個步驟中，您已定義倉儲庫存補充訊息結構描述。  

## <a name="next-steps"></a>後續步驟  
 您會定義要求拒絕訊息結構描述。  

## <a name="see-also"></a>另請參閱  
 [步驟 1： 建立 EAISchemas 專案](../core/step-1-create-eaischemas-project.md)   
 [步驟 3： 建立拒絕要求結構描述](../core/step-3-create-the-request-decline-schema.md)   
 [步驟 4： 建立對應](../core/step-4-create-the-map.md)   
 [步驟 5： 建置 Eaischema 專案](../core/step-5-build-the-eaischemas-project.md)   
 [使用 BizTalk 編輯器建立結構描述](../core/creating-schemas-using-biztalk-editor.md)   
 [關於 BizTalk 訊息內容屬性](../core/about-biztalk-message-context-properties.md)

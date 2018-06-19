---
title: 組態資訊 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Call Rules shape [Orchestration Designer], planning
- Call Rules shape [Orchestration Designer], configuring
ms.assetid: aa4924c6-4270-473b-aa0a-6d8b18375a39
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9a35767815eaf7406a7baae5d9dccb833492287
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233462"
---
# <a name="configuration-information"></a>組態資訊
本主題描述如何設定**呼叫規則**圖形。  
  
## <a name="orchestration-variables-and-fact-types"></a>協調流程變數和事實類型  
 在協調流程其中**呼叫規則**圖形所在，您必須具有符合原則中所使用的類型的變數。 若您的變數類型不正確，就無法提供正確的參數給原則。 假設您有**呼叫規則**圖形在協調流程為 CallMyRules，且您使用 CallMyRules 來呼叫 MyPolicy。 若在 MyPolicy 中使用的 .NET 類別為 MyClass，則您必須在協調流程中建立 MyAssembly.MyClass 類型的變數。 同樣地，若 MyPolicy 擁有**DataConnection**繫結，您必須建立的變數**Microsoft.RuleEngine.DataConnection**協調流程中的型別。  
  
 除了在協調流程內建立變數，您還必須為這些範圍變數建立執行個體。 您可以藉由新增**運算式**圖形至協調流程。 使用上述範例中，您必須產生 MyAssembly.MyClass 執行個體和**DataConnection**執行個體。 具現化**DataConnection**執行個體，執行下列動作：  
  
-   建立**SqlConnection**執行個體，並將它指派給 MySqlCon。  
  
-   建立**DataConnection**執行個體，並將它指派給 dataConnection (變數**DataConnection**類型)，如下列程式碼片段所示：  
  
    ```  
    dataConnection = new Microsoft.RuleEngine.DataConnection("NameOfSqlDatabaseHere", "NameOfYourTableHere", MySqlCon);  
    ```  
  
> [!NOTE]
>  如果沒有相符的事實類型的變數，這些類型不會出現在參數**指定原則參數**清單方塊中的 **[CallRules 原則組態**] 對話方塊。  
  
> [!NOTE]
>  協調流程引擎會自動轉換做為參數，BRE 原則到您指定的訊息變數**TypedXmlDocument**物件，並將它們判斷提示至規則引擎執行原則之前的工作記憶體。 因此，您不需要像處理 .NET 和資料庫事實一樣，宣告 TypedXmlDocument 型別的變數。  
  
## <a name="message-type-and-document-type"></a>訊息類型和文件類型  
 您必須確定**DocumentType** （您所實作的商務規則編輯器 」 中） 您的商務規則中使用的 XML 節點的屬性等同於**MessageType**中定義這些 XML 節點協調流程，它必須符合**MessageType**訊息或訊息部分，將會傳遞至規則引擎中的**呼叫規則**圖形。  
  
 例如，如果您在 BizTalk 專案中，定義訂單 (PO) XML 結構描述**MessageType**針對此結構描述定義**BTSProject.PO** (如果**BTSProject**是命名空間或使用預設命名空間的專案名稱）。  
  
 如果是**PO\Amount**項目，才能卸除到規則定義，您必須變更其**DocumentType**屬性**BTSProject.PO**中 [屬性] 視窗. 選取結構描述中的任何節點上時，您可以存取 屬性 視窗**XML 結構描述** 索引標籤 事實總管 中的。 此變更會套用至結構描述中的所有項目，但並不會隨著結構描述而儲存。 在啟動「商務規則編輯器」或重新載入結構描述後，必須將它重設。 根據 XML 結構描述或直接從 XML 結構描述建置的規則，此動作對於詞彙定義而言是必要的。 如果不這麼做，您仍然可以執行原則，但**呼叫規則**圖形將無法正常運作，並不會出現在訊息類型**指定原則參數**清單方塊中的 **[CallRules 原則組態**] 對話方塊。
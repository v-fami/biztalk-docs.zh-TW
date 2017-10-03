---
title: "內容屬性檢視 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking Profile Editor, message schemas
- Context Property view [Tracking Profile Editor]
- Tracking Profile Editor, Context Property view
- message schemas, XML messages
ms.assetid: 17a21b86-995c-4dc2-9a3c-1309837d0b9b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84a0f3a1d507e1440f67cd5f9e4afa18bff0b52a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="context-property-view"></a>內容屬性檢視
[內容屬性] 檢視會顯示與屬性相關聯的 XML 訊息結構描述。 您可以從 [協調流程排程] 檢視中某些圖形的捷徑功能表存取該檢視。  
  
## <a name="working-with-the-context-property-view"></a>使用內容屬性檢視  
 選取內容屬性檢視，請按一下**選取事件來源**按鈕，然後按一下**選取內容屬性**功能表項目。 接著從已知的內容屬性清單中選擇內容屬性，以載入該屬性的結構描述。 一旦選取屬性後，您可以將項目從關聯的結構描述拖曳到活動的資料項目資料夾，表示要由位於此動作的訊息中特定之 XPath 運算式擷取該資料。  
  
 在協調流程排程檢視中，以滑鼠右鍵按一下含有內容屬性的圖形亦可開啟內容屬性檢視。 這會開啟內容功能表，您可從中按一下**內容屬性結構描述**功能表項目，來擷取與圖形相關聯的內容屬性的清單。  
  
 可用的內容屬性清單可能很長。 如果您知道您要搜尋的屬性名稱的一部分，您可以輸入在**中字串**文字方塊中，然後按一下**搜尋** 按鈕。 這樣就會只選取名稱中包含所輸入之部分字串的屬性。  
  
> [!NOTE]
>  當您選擇經由 [內容屬性] 檢視進行對應時，可能的屬性結構描述清單將會是 BizTalk Server 安裝中已設定之每個屬性結構描述的完整清單。  請務必注意，所呈現的結構描述未能判別目前執行中的處理程序，使用了哪些 BizTalk Server 功能。 例如，您可以從 [內容屬性] 對應所提供的結構描述清單中選取 SOAP 屬性的結構描述，但是執行中的處理程序本身可能不使用 SOAP。 經由未使用的屬性所對應的任何 BAM 活動項目，將導致 BAM 擷取到空值或空白資料。  
  
## <a name="see-also"></a>另請參閱  
 [什麼是事件來源檢視時？](../core/what-is-the-source-event-view.md)   
 [追蹤設定檔編輯器](../core/tracking-profile-editor.md)
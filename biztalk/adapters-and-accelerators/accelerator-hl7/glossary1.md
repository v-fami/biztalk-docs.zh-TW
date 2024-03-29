---
title: HL7 加速器，BizTalk Server 中的詞彙 |Microsoft Docs
description: 一般詞彙和定義了解，並了解如何使用 BizTalk Accelerator for HL7
ms.custom: ''
ms.date: 08/16/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ffb9c18a-5fe5-448f-b115-0973e9d12952
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b632f494766974079ec13dd0803ae776c96adfe2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997879"
---
# <a name="glossary"></a>詞彙
Microsoft BizTalk Accelerator for HL7 會使用下列詞彙和定義。

## <a name="a"></a>只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，    
 **成品**    
 構成 HL7 V3.0 選票成品可探索、 分析和設計活動導致訊息規格建立所產生的交付項目。  
  
 HL7 V3.0 標準內文件所組成的元件是成品。 這包括分鏡腳本、 應用程式角色、 觸發程序事件、 領域訊息資訊模型規格 (D-MIMs)、 精簡的訊息資訊模型規格 (R MIMs)、 階層式的訊息描述 specificatins(HMDs)、 訊息類型和互動。  
  
 **成品識別碼**    
 Technical Committee 送出，並提供每個成品由串連子區段、 網域和成品的程式碼、 6 位數、 無意義的數字，2 位數的領域程式碼和 2 位數的版本號碼指派的唯一識別碼。  

## <a name="c"></a>c
  
 **基數**    
 資料元素 （資料元素可能會重複次數內的物件檢視的個別發生次數） 或階層式的訊息描述 （最小和最大數目的項目之訊息項目） 中的資料行的屬性。 請參閱階層式的訊息描述。  
  
## <a name="d"></a>D   
 **網域**    
 1. 問題的一組 HL7 訊息或 （「 應用程式網域 」） 的系統處理的主旨。 健康照護中感興趣的特定區域。 
 2. 可能的值的資料型別、 屬性或資料類型的元件組。 請參閱詞彙網域。 
 3. HL7，例如 Pharmacy 實驗室，病患管理內專題討論群組。  
  
## <a name="e"></a>E 
 **事件**    
 1. 刺激造成值得注意的狀態變更的物件。 叫用物件的行為訊號。 請參閱觸發程序事件。 
 2. 情緒詞彙網域值。  
  
 
## <a name="h"></a>H
**階層式的訊息描述 (HMD)**    
 訊息及其群組、 序列、 選擇性和基數的確切欄位規格。 含有一或多個互動的訊息類型，或代表一或多個常見的訊息項目類型。 這是主要標準 HL7 訊息結構。  
  
## <a name="m"></a>M  
 **必要項目**    
 階層式訊息描述 (HMD) 資料行。 如果屬性強制性，此屬性為基礎的所有訊息項目包含必須包含非 null 值，或必須有預設值不是 null。  
  
  
 **訊息**    
 從應用程式的不同而不同，傳達的資訊套件。 請參閱訊息類型和訊息執行個體。  
  
 **訊息的開發架構 (MDF)**    
 模型、 方法和工具構成指定 HL7 V3.0 訊息的方法集合。 HL7 標準的開發人員使用此架構。 V3.0 指南摘要說明內容的方法。  
  
 **訊息項目**    
 結構內的訊息類型的單位。  
  
 **訊息項目類型**    
 訊息類型，描述其中一個項目訊息的部分。  
  
 **訊息執行個體**    
 格式化為特定的傳輸訊息。 相同的訊息類型可以描述兩個訊息和識別具有相同的互動和尚未改變執行個體中因為變化值、 目前狀態，或不存在，正在傳送的資料和不同基數的集合。 否則相同的訊息可能會不同執行個體，如果在不同時間或依不同的寄件者傳送。  
  
 **訊息內容**    
 資料執行中的訊息。  
  
 **訊息類型**    
 指定在階層式訊息描述 (HMD) 的訊息項目組織。 每個訊息類型會與溝通互動模型中的一或多個互動的一部分。 訊息類型實際上會構成一組建構訊息，提供一組特定的執行個體資料的規則。 它也會定義用於剖析訊息，以復原的執行個體資料的規則。 訊息類型無關實作的技術規格，因此，如果相同的資料會使用相同的訊息類型和不同的實作技術規格，可以從兩個不同中音譯訊息類型。  

## <a name="p"></a>P  
 **屬性**    
 任何屬性、 關聯、 方法或類別或物件定義的狀態模型。 在 HMD，資料行表示的類別、 屬性或關聯角色名稱，因為它會顯示參考資訊模型 (RIM) 中。  

## <a name="r"></a>R  
 **參考資訊模型 (RIM)**    
 從其他所有資訊模型 (例如 MIMs R) 和訊息衍生 HL7 資訊模型。  
  
 **調整過的訊息資訊模型 (R MIM)**    
 表示一組訊息的需求資訊結構。 可能包含從 RIM 類別，會複製的其他類別的邊緣條件約束的子集。 包含支援一或多個階層式訊息描述 (HMDs) 所需的類別、 屬性、 關聯和資料型別。 單一訊息，可顯示為透過 R MIM 內類別的特定路徑。  

## <a name="s"></a>S  
 **案例**    
 在統一的模型化語言 (UML)，「 執行透過單一使用案例的單一路徑 」。 陳述式的定義為一連串的互動中醫療保健相關的事件。 案例提供一組模型 committee 預期通常發生在網域中的互動。 通常，循序圖來顯示單一案例的互動的一組建構。 每個案例中會顯示為互動模型的子集。  
  
 **schema**    
 1. 圖表的簡報、 結構化的架構或計劃。 
 2. 一組需求，必須符合才能讓文件或資料集是內容中的該語法有效的運算式。 XML 結構描述是規格中標準通用標記語言 (SGML) 的文件的結構或資料集。

## <a name="next-steps"></a>後續的步驟
[合作對象 - BTAHL7 設定總管](parties-tab.md)  
[全域設定 - BTAHL7 設定總管](global-settings-tab.md)  
[MLLP 傳輸屬性對話方塊 UI 說明](mllp-transport-properties-dialog-box-ui-help.md)
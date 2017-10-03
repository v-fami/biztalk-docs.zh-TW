---
title: "BAM 開發人員概念 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c26d0aed-821c-4e1f-9cc9-9375a2ba28de
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e407121e9f71707b45f95e77a8520ed30df3b33
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bam-concepts-for-the-developer"></a>開發人員適用的 BAM 概念
身為 BAM 開發人員，您必須熟悉重要的 BAM 概念，例如活動、接續和參考等。 您也應該瞭解追蹤和交易式處理兩者之間的差異。  
  
## <a name="what-is-a-bam-activity"></a>何謂 BAM 活動？  
 BAM 活動是商務程序 (例如單一 PO) 中對某個項目而言有意義之資料內容的定義； 它定義了 BAM 資料庫中的資料行。  
  
 活動執行個體代表商務中的工作單位，例如訂單或貸款申請。 活動則指定一份里程碑清單 (活動的歷程記錄) 和有意義的資料。 活動執行個體在 BAM 主要匯入資料庫中是以單一資料列來表示。 該活動執行個體的任何資料項目都只有一個值。  
  
 活動可用來對商務使用者或資訊工作者顯示有關此工作單位的歷程記錄 (里程碑) 和資料。 例如，BAM SDK 範例中定義的活動包含諸如「已付」及「傳送」等里程碑，以及如「總金額」等有意義的資料。  
  
 BAM 活動通常會直接對應到商務程序，但是在高階抽象概念中，活動與您 IT 基礎結構的實際實作無關。  
  
 身為開發人員的工作，就是只從特定活動內容中的實作公開相關的里程碑和資料。  
  
## <a name="what-is-a-continuation"></a>何謂接續？  
 接續提供有關下列資訊的 BAM 基礎結構指導：  
  
-   預期的事件發生順序  
  
-   處理唯一識別碼任何變更的方法，此識別碼與事件項目相互關聯  
  
 如需接續及其使用方式的詳細資訊，請參閱[Continuation 和 ContinuationID 節點](../core/continuation-and-continuationid-nodes.md)。  
  
## <a name="what-is-a-reference"></a>何謂參考？  
 參考 (也稱為相關活動) 會指定活動與其他項目之間的關係。 相關項目的範例包括其他項目或文件位置。  
  
> [!NOTE]
>  當您將某個活動指定為相關活動時，如果相關活動尚未完成，並不會妨礙系統完成目前的活動；這一點與接續活動不同。  
  
## <a name="tracking-and-transactional-processing"></a>追蹤和交易式處理  
 撰寫 BAM 程式碼可以讓您控制追蹤資料的方式，也就是透過追蹤或交易式處理來進行追蹤。 根據預設，BAM 會為追蹤和處理指定同等的重要性。 這表示如果追蹤功能或交易程序失敗，兩者都將無法繼續執行。 追蹤資料庫中不會記錄任何內容，而交易也會回復。 這可能不是您的解決方案慣用的追蹤方法。 透過開發 BAM，您可以決定追蹤或交易式處理何者優先順序較高。  
  
 下表說明在 BAM 中追蹤資料的模式。  
  
|狀況|[描述]|  
|--------------|------------------|  
|追蹤優先於處理|如果處理程序成功，則寫入追蹤資訊。<br /><br /> 如果處理程序失敗，則寫入有關失敗的資訊。|  
|處理等同於追蹤|如果追蹤或處理失敗，則回復所有動作。|  
|處理優先於追蹤|如果處理程序成功但追蹤功能失敗，則繼續處理。|
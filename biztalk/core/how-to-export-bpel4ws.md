---
title: 如何匯出 BPEL4WS |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BPEL4WS, exporting
- BPEL4WS, restrictions
- orchestrations, BPEL4WS
ms.assetid: 4648dfcf-cf48-4471-b088-07252c080fb8
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b16c2e34b498a9fb8d5fd3f6e69f022c2876a763
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22253830"
---
# <a name="how-to-export-bpel4ws"></a>如何匯出 BPEL4WS
您可以將現有的 BizTalk 協調流程匯出至 BPEL4WS。  
  
> [!IMPORTANT]
>  這個版本的 BizTalk Server 支援 BPEL4WS 1.1。 您不能匯入或匯出 BPEL4WS 1.0。  
  
 當您匯出時，供編譯的 BPEL4WS 規範要求協調流程只能包含 XLANG/s 和 BPEL4WS 之間通用的功能，或可以轉譯為 BPEL4WS 且不影響行為的功能。  
  
## <a name="export-restrictions-on-orchestrations-for-bpel4ws-compliance"></a>BPEL4WS 規範的協調流程匯出限制  
  
-   您不能使用 [呼叫協調流程] 圖形或 [啟動協調流程] 圖形。  
  
-   您不能使用 [轉換] 圖形。  
  
-   您不能在自訂 .NET 元件叫用方法。  
  
-   您不能將逾時套用到長時間執行的交易。  
  
-   您的協調流程不能接受參數。  
  
-   可呼叫的補償處理常式不能有參數。  
  
-   XPATH 必須能夠支援變數類型。  
  
-   您不能使用 [擱置] 圖形。  
  
-   常值必須為下列其中一種類型：  
  
     boolean、char、byte、sbyte、int32、uint32、int64、uint64、single、double、string  
  
-   算術運算子只允許出現在下列數字型別的運算元：  
  
     byte、sbyte、int32、uint32、int64、uint64、single、double  
  
-   char 類型不能使用關係運算子。  
  
-   您不能參考運算式中的服務連結屬性。  
  
-   您無法執行任何動作之間**傳送**圖形和**接收**使用相同的輸出要求-回應連接埠的圖形。  
  
-   您不能間接參考 Web 服務，像是透過參考包含參考的另一個專案。 您必須明確參考您的專案中之 Web 服務。  
  
-   您不能在延遲中指定常數 DateTime 或 TimeSpan。 而是要使用 System.Xml 命名空間中的其中一個轉換類別：  
  
     常數 DateTime：System.Xml.XmlConvert.ToDateTime，例如 System.Xml.XmlConvert.ToDateTime("2004-04-15")  
  
     常數 TimeSpan：System.Xml.XmlConvert.ToTimeSpan，例如 System.Xml.XmlConvert.ToTimeSpan("2004-04-15")  
  
> [!NOTE]
>  字元常值匯出為不帶正負號的整數。 例如，'a' 匯出為 97，'b' 匯出為 98 等等。  
  
> [!CAUTION]
>  識別項名稱必須符合 W3C「可延伸標記語言」(XML) 1.0 規格。  
  
#### <a name="to-export-an-orchestration-to-bpel4ws"></a>將協調流程匯出至 BPEL4WS  
  
1.  將類型為 BizTalk 協調流程的新項目加入您的專案。  
  
2.  按一下設計介面，以顯示 [協調流程屬性] 視窗。  
  
3.  設定**模組可匯出**為 True。  
  
4.  您想要用於命名空間中的型別**模組 XML 目標命名空間**。  
  
5.  設定**協調流程可匯出**為 True。  
  
6.  您想要用於命名空間中的型別**協調流程 XML 目標命名空間**。  
  
7.  在 [方案總管] 中，使用滑鼠右鍵按一下協調流程的 .ODX 檔案。  
  
8.  選取**匯出到 BPEL**。  
  
     您的協調流程會匯出到 BPEL4WS。 請參閱 [輸出視窗] 和 [工作清單]，以確認成功或診斷問題。 若匯出成功，則 .WSDL 檔案和 .BPEL 檔案會建立在您的專案目錄中。  
  
> [!NOTE]
>  若您的協調流程包含對角色連結 (服務連結) 的指派或對動態連接埠的常值指派，則 BizTalk 會產生空的 BPEL4WS 結束點參考並產生警告。  
  
## <a name="see-also"></a>另請參閱  
 [如何匯入 BPEL4WS](../core/how-to-import-bpel4ws.md)   
 [XLANG-s 至 BPEL4WS 型別轉換](../core/xlang-s-to-bpel4ws-type-conversions.md)
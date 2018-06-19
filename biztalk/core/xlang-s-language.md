---
title: XLANG 的語言 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, properties
ms.assetid: 97b62f17-5a8d-4d87-8563-1f6d941f027f
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2329d4bc42617d70227481a0d70064d368f3c0e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22290910"
---
# <a name="xlang-s-language"></a>XLANG 的語言
XLANG/s 設計為可使用網際網路標準 (如 XML、XSD 和 Web 服務描述語言 (WSDL))，而且具有內嵌支援來處理 .NET 物件和訊息。 XLANG/s 可視為具有某些 C# 運算式功能的訊息語言。 但是，XLANG/s 與 C# 之間無法移植程式碼。  
  
 XLANG/s 鼓勵在處理與實作之間有清楚的分隔， 例如，在 XLANG/s 中指定商務程序或通訊協定，並在其他 .NET 程式語言 (如 C# 或 Visual Basic .NET) 中實作應用程式的本機層面 (如資料庫存取)。  
  
 XLANG/s 的指派和運算式語法是以 C# 當做模型，而且您應該參考 C# 規格，以瞭解精確的語法。 XLANG/s 定義了一組豐富的高層級構造，這組構造是用來定義商務程序。 雖然 XLANG/s 提供支援，如字串與整數類的低階資料類型，也會定義高層級的資料類型： 訊息、 連接埠、 相互關聯，以及服務連結。 這些資料類型用來嚴格定義與商務程序相關聯的語意，和會輔以處理序控制陳述式例如**時**或**範圍**。  
  
 XLANG/s 陳述式通常分為兩種類別： 簡單的陳述式會處理其本身，例如**接收**或**傳送**，和包含或是分組任一個簡單的陳述式的複雜陳述式或其他複雜的陳述式，例如**範圍**，**平行**，和**接聽**。 以 XLANG/s 具體化的語意是用來反映「Web 服務商務程序執行語言」(BPEL4WS) 規格所定義的語意 (此規格是由 Microsoft、IBM 和 BEA 針對商務程序語意的定義所發佈)。  
  
 您可以選擇瞭解 XLANG/s 的主要構造，因為在 BizTalk 協調流程設計師中繪製協調流程圖時，會產生這些構造。 協調流程設計師是一個功能豐富的圖形工具，可以視覺方式來設計商務程序。 它會產生 XLANG/s 檔案，這些檔案具有 .odx 副檔名，而且其標頭中包含其他視覺資訊，本文中則包含自訂屬性資訊。  
  
> [!NOTE]
>  XLANG/s 語言是專屬的，而且未完整記錄。 本章節會公開當您開發協調流程時，可能需要注意的某些語言部分。 不支援直接修改 .odx 檔案。  
  
## <a name="xlangs-programs"></a>XLANG/s 程式  
 最簡單的 XLANG/s 程式需要定義訊息類型，這樣可為協調流程提供一些資料來開始使用。 協調流程會透過連接埠接收訊息，然後終止。 下列程式碼是一個範例：  
  
```  
module HelloWorldApp  
{  
     private porttype ptPOReceive  
     {  
      oneway opPOReceive  
      {  
       HelloWorldApp.PurchaseOrder  
      }  
     }  
     private porttype ptPOSend  
     {  
      oneway opPOSend  
      {  
       HelloWorldApp.PurchaseOrder  
      }  
     }  
     private service  HelloWorld  
     {  
      port implements HelloWorldApp.ptPOReceive poPOReceive;  
      port uses HelloWorldApp.ptPOSend poPOSend;  
      message HelloWorldApp.PurchaseOrder msgPO;  
      body ()  
      {  
       activate receive (poPOReceive.opPOReceive, msgPO);  
       send (poPOSend.opPOSend, msgPO);  
       }  
     }  
}  
```  
  
 在上面的 XLANG/s 程式中，`module` 關鍵字會定義 XLANG/s 程式的編譯單位。 在程式中使用的所有類型 — 例如**porttype**， **correlationsettype**， **servicelinktype**，和**messagetype**— 設定於此層級。  
  
 連接埠是 XLANG/s 可以傳送或接收訊息、 或的建構和連接埠有定義的類型，稱為**porttype**。 **Porttype**建構可定義可用的連接埠的作業的集合。 這些作業會定義透過此連接埠的單一有效訊息交換。 定義**porttype**， **messagetype**， **servicelinktype**，或**correlationsettype**建構，XLANG/s 的作者程式基本上建立複雜資料型別定義。 這些定義具有相同的優點與其他語言中複雜資料型別： 它們抽象概念卻中較高的層級的資料類型，而且可讓使用者容易重複使用的資料類型。  
  
 **PtPOReceive**中之前 HelloWorldApp 模組會定義為單向連接埠接收連接埠作業**opPOReceive**。 HelloWorld 服務區塊會定義此程序的實際實作以及它可能使用的任何變數 (包括連接埠和訊息變數)。 在這個區塊的程式碼的第一次三行定義的連接埠變數**poPOReceive**和**poPOSend**和訊息**msgPO**分別。 本文包含的程式碼會描述此服務和執行行為的參數。 所有的變數 (除非以巢狀範圍區塊定義) 都是以這個層級為範圍。 Receive 陳述式，這是一項啟動接收，接收**msgPO**訊息從**Msgpo**連接埠，建立協調流程的新執行個體。 當收到訊息之後，傳送陳述式會將此訊息導向傳送埠。 在上述程式碼中的兩個連接埠宣告**poPOReceive**使用 implements 修飾詞，而**poPOSend**使用 uses 修飾詞。 implements 修飾詞會告訴執行階段，它將要透過該連接埠來接收訊息。 uses 修飾詞會告訴執行階段，它將要透過該連接埠來傳送訊息。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [XLANG 的資料型別](../core/xlang-s-data-types.md)  
  
-   [XLANG s 陳述式](../core/xlang-s-statements.md)  
  
-   [XLANG 的變數和運算子](../core/xlang-s-variables-and-operators.md)  
  
-   [XLANG 的運算式](../core/xlang-s-expressions.md)  
  
-   [XLANG s 保留字](../core/xlang-s-reserved-words.md)  
  
-   [XLANG-s 至 BPEL4WS 型別轉換](../core/xlang-s-to-bpel4ws-type-conversions.md)  
  
## <a name="see-also"></a>另請參閱  
 [關於 BizTalk 協調流程引擎](../core/about-the-biztalk-orchestration-engine.md)
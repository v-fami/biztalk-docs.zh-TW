---
title: WCF 配接器 FAQ： 使用 WCF 服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: befa2268-8a65-465f-8086-70a66808845e
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41d02fe0b7be1f53edaac4c18cfd7717a25c3a71
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="wcf-adapter-faq-using-wcf-services"></a>WCF 配接器 FAQ：使用 WCF 服務
## <a name="how-does-biztalk-server-use-its-wcf-adapters-to-access-wcf-services"></a>BizTalk Server 如何使用其 WCF 配接器存取 WCF 服務  
 在 BizTalk Server 中，BizTalk WCF 配接器是透過 WCF 接收位置或傳送埠設定。 啟用使用 WCF 配接器的接收位置時，會針對每個接受位置產生並初始化單一 ServiceHost 執行個體。 ServiceHost 執行一般的服務會接受內送 WCF 訊息，並將它們轉換成 BizTalk 訊息中，它們發佈到 BizTalk MessageBox 資料庫之前。 一般的 ServiceHost 服務是內部 WCF BizTalk 接收配接器實作並公開無類型合約。 在 WCF 中，無類型合約所組成，採用單一參數的型別 WCF System.ServiceModel.Channel.Message 作業簽章。  
  
 WCF 服務的作業應該標示為 IsOneWay = false，若要存取 BizTalk 傳送埠，即使不沒有傳回任何資料。 用戶端合約上的作業加以註解 isoneway = false 和 ReplyAction ="*"。  此外應標示為從用戶端的所有呼叫，在 IsOneWay ="false"。 雙向服務作業可能會傳回訊息類型的值。 例外，它使用 Wcf-netmsmq 配接器，因為它會執行將訊息張貼到 MSMQ 佇列為單向作業。 在此情況下，傳送埠可以是單向和任何服務作業標示為 IsOneWay = true。  
  
 可能會有點複雜，也可能是在 WCF 中定義 isOneWay = false OperationContract 實際上會傳回 void 的方法。 在這種情況沒有實際傳回為您建立由 WCF 執行階段在網路上的訊息。  
  
 BizTalk WCF 配接器進行這項功能的使用。 當您指定單向 BizTalk 連接埠實際取得 void 的方法為 isOneWay = false 內 WCF 配接器的實作。 重點是，BizTalk 單向連接埠，當使用直接通道，例如 HTTP 或 net.tcp，實際上會對應 isOneWay = false 的 OperationContract。 已排入佇列的通道，例如 net.msmq 都不同，因為單向 BizTalk 連接埠發生與 isOneWay = true 的 OperationContract。 因為 WCF 發送器使用對通道的交易，是不同的情況。  
  
## <a name="how-do-you-create-and-use-a-custom-binding-with-a-wcf-custom-adapter"></a>您該如何建立及使用 WCF 自訂配接器的自訂繫結？  
 WCF CustomBinding 的 Bindingelement 集合所組成。 可以建立 CustomBinding 彙整預先存在的 Bindingelement （例如，結合從其他來源的預先存在的編碼器的現存傳輸）。 或在建立藉由組合預先存在的新撰寫自訂 BindingElement BindingElement。 在程式碼中 CustomBinding 可以從建立這些元件 bindingelements 來以程式設計方式加入。 WCF 也可讓這個結構中的透過.NET 組態 （設定檔）。 使用 BizTalk Server 便可以透過 BizTalk WCF 自訂配接器建立此 CustomBinding。  
  
 BizTalk WCF 自訂配接器不僅可讓您從 [bindingelements] 來建立新的繫結，也可讓您設定的新繫結直接。 它也可讓您設定標準繫結上的行為。 這是特別有用，因為比起撰寫新的 Bindingelement 物件更容易撰寫自訂行為。  
  
 建立 BindingElement 是涉及的開發的活動，而其參考的最佳資源來源是超連結的 WCF 範例 」http://go.microsoft.com/fwlink/?LinkId=142449"\t"_blank" http://go.microsoft.com/fwlink/?LinkId=142449。 若要建立自訂 BindingElement 您建立衍生自 BindingElement 類別。 新的 BindingElement 將一定要在新的組件。 這個組件必須安裝到全域組件快取 (GAC) 的 BizTalk 主控件，其中傳送埠和接收位置的管理電腦設定。 若要建立自訂繫結關聯的特定傳送埠或接收位置，您必須先將它加入至\<bindingElementExtensions\>在同一部電腦上的 machine.config 檔案的區段。  
  
 完成帶出該變更之後 **傳輸內容設定** 對話方塊來設定繫結。  
  
1.  在 **繫結** 索引標籤的 選取的繫結類型 **customBinding**。  
  
2.  在 **繫結**  窗格中，以滑鼠右鍵按一下 **CustomBindingElement**, ，然後選取 **加入擴充**。  
  
3.  選取您在 machine.config 檔案中指定的繫結項目，並視需要設定繫結。 您已經準備好用於訊息傳送或接收。  
  
 加入這種方式時，BizTalk 將會非常有限的自訂繫結驗證。 因此，務必確定正確的順序列出繫結項目。 您想要在執行階段的第一次叫用的繫結元素必須位於 CustomBindingElement 繫結樹狀結構，在對話方塊底部。 Bindingelement 清單必須包含傳輸，而且該傳輸必須位於清單的底部。 Bindingelement 組也可能包含編碼器。 如需詳細資訊，請參閱 < WCF 文件上繫結項目在[ http://go.microsoft.com/fwlink/?LinkId=142449 ](http://go.microsoft.com/fwlink/?LinkId=142449)。  
  
## <a name="what-is-a-wcf-custom-behavior-and-how-do-i-use-one-with-biztalk-server"></a>什麼是 WCF 自訂行為，以及如何使用一個 BizTalk Server？  
 使用 WCF 做為訊息的通訊機制的優點是能夠使用自訂程式碼來擴充其服務的功能。 自訂行為延伸模組是 WCF 區別在市場上其他 Web 服務技術的功能。  
  
 有攔截，並執行自訂處理的訊息抵達最後目的地之前 WCF 訊息的流程中的不同點。 WCF 自訂行為延伸模組是一個這種類型的攔截機制，而且可用來擴充 WCF 服務或用戶端功能，在不同層級的資料粒度。 WCF 服務和用戶端層級也都可以自訂行為延伸模組。 設定 WCF 服務的呼叫堆疊上的行為並不會影響用來進行呼叫的通訊繫結。 事實上，行為通常不會對用戶端因為它們不會顯示在服務發行的中繼資料。 用戶端通常都不曉得 WCF 作業呼叫期間執行的行為。  
  
 輕鬆地實作自訂中呼叫 WCF 服務的處理能力是通訊的 WCF 為何這類豐富的程式設計開發架構相較於其他的 Web 應用程式之間方式的主要原因之一。 這個自訂程序可能需要幾乎任何形式，由 Web 應用程式中的擴充性需求。 開發人員可以建立自訂延伸，檢查並驗證服務設定或修改 WCF 用戶端和服務應用程式中的執行階段行為。 行為可以補充一般訊息處理、 修改訊息處理期間、 詳細檢查特定設定的條件，以及採取適當的動作、 驗證呼叫者的身分識別以及是否成功，會將訊息傳遞。因為它真正是自訂處理機制實作任何擴充性應用程式需要。  
  
 若要使用 WCF 自訂行為，BizTalk Server 中您將設定使用 **行為** Wcf-custom 或 Wcf-customisolated 配接器的接收位置或傳送埠 索引標籤。
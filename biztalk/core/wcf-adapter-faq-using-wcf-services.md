---
title: "WCF 配接器 FAQ： 使用 WCF 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: befa2268-8a65-465f-8086-70a66808845e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41d02fe0b7be1f53edaac4c18cfd7717a25c3a71
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="wcf-adapter-faq-using-wcf-services"></a>WCF 配接器 FAQ：使用 WCF 服務
## <a name="how-does-biztalk-server-use-its-wcf-adapters-to-access-wcf-services"></a>BizTalk Server 如何使用其 WCF 配接器存取 WCF 服務  
 在 BizTalk Server 中，BizTalk WCF 配接器是透過 WCF 接收位置或傳送埠設定。 啟用使用 WCF 配接器的接收位置時，會針對每個接受位置產生並初始化單一 ServiceHost 執行個體。 ServiceHost 執行接受內送 WCF 訊息，並將它們轉換成 BizTalk 訊息中，然後再發行到 BizTalk MessageBox 資料庫的一般服務。 一般的 ServiceHost 服務是內部 WCF BizTalk 接收配接器實作並公開無類型合約。 在 WCF 中，無類型合約所組成，接受一個參數的型別 WCF System.ServiceModel.Channel.Message 作業簽章。  
  
 WCF 服務的作業應該標示為 IsOneWay = false，若要存取 BizTalk 傳送埠，即使沒有任何要傳回的資料。 用戶端合約上的作業加以註解為 IsOneWay = false 和 ReplyAction ="*"。  此外從用戶端的所有呼叫應標示都為在 IsOneWay ="false"。 雙向服務作業可能會傳回值類型的訊息。 由於它會執行將訊息張貼到 MSMQ 佇列為單向作業，此例外狀況使用 Wcf-netmsmq 配接器。 在此情況下，傳送埠可以是單向和任何服務作業標示為 IsOneWay = true。  
  
 可能會有點混淆，所以也可以在 WCF 中定義了 isOneWay = false OperationContract 實際上會傳回 void 的方法上。 在這種情況會實際傳回為您建立由 WCF 執行階段在網路上的訊息。  
  
 BizTalk WCF 配接器進行這項功能的使用。 當您指定單向 BizTalk 連接埠實際上取得 void 方法為 isOneWay = false 內 WCF 配接器的實作。 重點是，BizTalk 單向連接埠，使用 HTTP 或 net.tcp，例如直接通道時實際對應至 isOneWay = false OperationContract。 例如 net.msmq 佇列的通道會不同，因為單向 BizTalk 連接埠，會發生與 isOneWay = true OperationContract。 這種情況是不同的因為 WCF 發送器使用對通道的交易。  
  
## <a name="how-do-you-create-and-use-a-custom-binding-with-a-wcf-custom-adapter"></a>您該如何建立並使用 WCF 自訂配接器的自訂繫結嗎？  
 WCF CustomBinding BindingElements 的集合所組成。 可以建立 CustomBinding 彙整預先存在的 BindingElements （例如，結合使用其他來源的預先存在的編碼器的既有傳輸）。 或藉由組合預先存在的新撰寫的自訂 BindingElement BindingElement 加以建立。 在程式碼中 CustomBinding BindingElements 這些元件從由建置以程式設計方式加入它們。 此外，WCF 也可讓透過.NET 組態 （組態檔） 的這個建構。 使用 BizTalk Server 可以透過 BizTalk WCF 自訂配接器建立此 CustomBinding。  
  
 BizTalk WCF 自訂配接器不僅可讓您建立新的繫結從 Bindingelement，也可讓您設定的新繫結直接。 它也可讓您設定標準繫結上的行為。 這是特別有用，因為寫入自訂行為會比撰寫新的 BindingElements 物件容易得多。  
  
 建立 BindingElement 是一項所涉及的開發工作，並參考它的最佳資源來源是超連結"http://go.microsoft.com/fwlink/?LinkId=142449"\t"_blank"http://go.microsoft.com/fwlink/?LinkId=142449 的 WCF 範例。 若要建立自訂的 BindingElement，您會建立衍生自 BindingElement 的類別。 新的 BindingElement 將必須在新的組件中。 這個組件必須安裝到全域組件快取 (GAC) BizTalk 主控件，其中傳送埠和接收位置的管理電腦的設定。 若要建立自訂繫結關聯的特定傳送埠或接收位置，您必須先將它加入至\<bindingElementExtensions\>在同一部電腦上的 machine.config 檔案的區段。  
  
 進行調出該變更後**傳輸屬性組態**對話方塊來設定繫結。  
  
1.  在**繫結**索引標籤上，繫結類型 選取**customBinding**。  
  
2.  在**繫結** 窗格中，以滑鼠右鍵按一下**CustomBindingElement**，然後選取**加入擴充**。  
  
3.  選取您在 machine.config 檔案中指定的繫結項目，並視需要設定繫結。 已備妥用於訊息傳送或接收。  
  
 已加入以這種方式時，BizTalk 將會非常有限的自訂繫結驗證。 因此，務必確保以正確的順序列出繫結項目。 您想要叫用第一次在執行階段的繫結元素必須是 CustomBindingElement 繫結樹狀結構，在對話方塊底部。 Bindingelement 的清單必須包含傳輸，而且該傳輸必須是清單的底部。 Bindingelement 組也可能包含編碼器。 如需詳細資訊，請參閱 < WCF 文件上繫結項目在[http://go.microsoft.com/fwlink/?LinkId=142449](http://go.microsoft.com/fwlink/?LinkId=142449)。  
  
## <a name="what-is-a-wcf-custom-behavior-and-how-do-i-use-one-with-biztalk-server"></a>什麼是 WCF 自訂行為，以及如何使用一個 BizTalk Server？  
 使用 WCF 訊息的通訊機制的優點之一是使用自訂程式碼來擴充其服務的功能的機會。 自訂行為延伸模組是 WCF 區別市面上的其他 Web 服務技術的功能。  
  
 沒有以攔截並執行自訂處理的訊息抵達最後目的地之前 WCF 訊息的流程中的不同點。 WCF 自訂行為延伸模組是一個這種類型的攔截機制，可用於延伸不同的資料粒度層級的 WCF 服務或用戶端功能。 WCF 服務和用戶端層級也都可以自訂行為延伸模組。 設定 WCF 服務呼叫堆疊上的行為已用來執行呼叫通訊繫結上的沒有影響。 事實上，這些行為屬於通常看不到用戶端，因為它們不會顯示在服務發行中繼資料。 用戶端通常會有不知道呼叫 WCF 作業期間執行的行為。  
  
 若要輕鬆地實作自訂中呼叫 WCF 服務的處理能力是通訊的 WCF 原因是通訊的這類的豐富程式設計典範相較於其他 Web 應用程式之間方式的主要原因之一。 這個自訂程序可以採用幾乎任何形式，由 Web 應用程式內的擴充性需求規定。 開發人員可以建立自訂延伸，檢查並驗證服務組態或修改 WCF 用戶端和服務應用程式中的執行階段行為。 行為可以補充一般訊息處理、 修改訊息在處理期間，檢查特定組態的準則和採取適當的動作、 驗證呼叫者身分識別及傳遞訊息上，如果成功，等。由於是真正的自訂處理實作任何擴充性機制，您的應用程式需要。  
  
 若要使用 WCF 自訂行為，BizTalk Server 中您會設定使用**行為**Wcf-custom 或 Wcf-customisolated 配接器的接收位置或傳送埠 索引標籤。
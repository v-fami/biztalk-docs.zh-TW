---
title: WCF 配接器 FAQ： 使用 WCF 服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: befa2268-8a65-465f-8086-70a66808845e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3dc7ae44fa6ef6722c0887f2c70a83f43d1bf5c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970047"
---
# <a name="wcf-adapter-faq-using-wcf-services"></a>WCF 配接器 FAQ：使用 WCF 服務
## <a name="how-does-biztalk-server-use-its-wcf-adapters-to-access-wcf-services"></a>BizTalk Server 如何使用其 WCF 配接器存取 WCF 服務  
 在 BizTalk Server 中，BizTalk WCF 配接器是透過 WCF 接收位置或傳送埠設定。 啟用使用 WCF 配接器的接收位置時，會針對每個接受位置產生並初始化單一 ServiceHost 執行個體。 ServiceHost 執行一般的服務，可接受內送 WCF 訊息，並將它們轉換成 BizTalk 訊息中，再將它們發佈至 BizTalk MessageBox 資料庫。 一般的 ServiceHost 服務是內部 WCF BizTalk 接收配接器實作並公開無類型合約。 在 WCF 中，無類型合約所組成，採用單一參數的型別 WCF System.ServiceModel.Channel.Message 作業簽章。  
  
 WCF 服務的作業應該標示為 IsOneWay = false，若要存取 BizTalk 傳送埠，即使沒有任何要傳回的資料。 用戶端合約上的作業應該要標註為 IsOneWay = false 和 ReplyAction ="*"。  此外應該標示為 IsOneWay 在從用戶端的所有呼叫 ="false"。 雙向服務作業可能會傳回型別訊息的值。 這個例外狀況使用 Wcf-netmsmq 配接器，因為它會執行將訊息張貼到 MSMQ 佇列的單向作業。 在此情況下，傳送埠可以是單向和任何服務作業標示為 IsOneWay = true。  
  
 可能會造成一些混淆，您也可在 WCF 中定義的 isOneWay = false 的 OperationContract，實際上會傳回 void 的方法上。 在這種情況會實際將為您建立 WCF 執行階段在網路上傳回的訊息。  
  
 BizTalk WCF 配接器進行這項功能使用。 當您指定單向 BizTalk 連接埠，實際取得 void 的方法為 isOneWay = false 內 WCF 配接器的實作。 重點是，BizTalk 單向連接埠，使用 HTTP 或 net.tcp，例如直接通道時將會實際對應到 isOneWay = false 的 OperationContract。 已排入佇列的通道，例如 net.msmq 會不同，因為單向的 BizTalk 連接埠連線真的中斷了對談 isOneWay = true 的 OperationContract。 這種情況是不同的因為 WCF 發送器會使用通道一筆交易。  
  
## <a name="how-do-you-create-and-use-a-custom-binding-with-a-wcf-custom-adapter"></a>您該如何建立及使用 WCF 自訂配接器的自訂繫結嗎？  
 WCF CustomBinding BindingElements 集合所組成。 CustomBinding 可以藉由一起提取預先存在的 BindingElements （例如，結合既有的傳輸與從其他來源的預先存在的編碼器） 建立。 或者，可以藉由組合預先存在的 BindingElement 與新寫入的自訂 BindingElement 建立。 在程式碼中 CustomBinding 可以建立從這些元件 BindingElements 以程式設計方式加入它們。 此外，WCF 也可讓透過.NET 組態 （組態檔） 的這個建構。 使用 BizTalk Server 可以透過 BizTalk WCF 自訂配接器建立此 CustomBinding。  
  
 BizTalk WCF 自訂配接器不僅可讓您從 BindingElements 建置新的繫結，也可讓您設定的新繫結直接。 它也可讓您設定標準繫結上的行為。 這是特別有用，因為比起撰寫新的 BindingElements 物件更容易撰寫自訂行為。  
  
 建立 BindingElement 是所涉及的開發活動，而其參考的最佳資源來源是超連結的 WCF 範例 」<http://go.microsoft.com/fwlink/?LinkId=142449>"\t"_blank" http://go.microsoft.com/fwlink/?LinkId=142449。 若要建立自訂 BindingElement，您會建立衍生自 BindingElement 類別。 新的 BindingElement 將必須在新的組件中。 這個組件必須安裝到全域組件快取 (GAC) 所在之 BizTalk 主控件中，傳送埠和接收位置的管理電腦的設定。 若要自訂繫結相關聯的特定傳送埠或接收位置，您必須先將它新增至\<bindingElementExtensions\>的同一部電腦上的 machine.config 檔案的區段。  
  
 之後您再啟動該變更**傳輸內容設定**設定的繫結 對話方塊。  
  
1. 在 **繫結**索引標籤的 繫結類型，選取**customBinding**。  
  
2. 在**繫結**窗格中，以滑鼠右鍵按一下**CustomBindingElement**，然後選取**加入延伸模組**。  
  
3. 選取您在 machine.config 檔案中指定的繫結項目，並視需要設定繫結。 您現可供使用的訊息傳輸或接收。  
  
   以這種方式新增時，BizTalk 就會執行非常有限的驗證，自訂繫結。 因此，務必確認繫結項目會列在正確的順序。 您想在執行階段的第一次叫用的繫結元素必須位於底部的 CustomBindingElement 繫結樹狀目錄中，在對話方塊中。 BindingElements 的清單必須包含傳輸和該傳輸必須位於清單底部。 BindingElements 集合也可能包含編碼器。 如需詳細資訊，請參閱 WCF 文件上繫結項目在[ http://go.microsoft.com/fwlink/?LinkId=142449 ](http://go.microsoft.com/fwlink/?LinkId=142449)。  
  
## <a name="what-is-a-wcf-custom-behavior-and-how-do-i-use-one-with-biztalk-server"></a>什麼是 WCF 自訂行為，以及如何使用一個 BizTalk Server？  
 使用 WCF 做為訊息的通訊機制的優點之一是使用自訂程式碼來擴充其服務的功能的機會。 自訂行為延伸模組是其中一個 WCF 區別市場中其他 Web 服務技術的功能。  
  
 有不同的點，來攔截和執行自訂處理的訊息抵達其最終目的地之前 WCF 訊息的流程中。 WCF 自訂行為延伸模組是一種這類類型的攔截機制，而且可用來擴充 WCF 服務或用戶端功能，在不同的層級的資料粒度。 自訂行為延伸模組可存在於這兩個 WCF 服務和用戶端層級。 設定 WCF 服務的呼叫堆疊上的行為並不會影響用來進行呼叫的通訊繫結上。 事實上，行為是用戶端通常不會看到它，因為它們不會顯示在服務發行中繼資料。 用戶端通常會有 WCF 作業呼叫期間執行的行為不知道。  
  
 輕鬆實作自訂中呼叫 WCF 服務的處理能力是通訊的 WCF 為何這類的豐富程式設計典範相較於其他的 Web 應用程式之間方法的主要原因之一。 這個自訂的處理可能需要幾乎所有形式，即會依照在 Web 應用程式的擴充性需求。 開發人員可以建立自訂的延伸模組，檢查及驗證服務組態或修改在 WCF 用戶端和服務應用程式的執行階段行為。 行為可以補充一般的訊息處理、 在處理期間修改訊息、 繁複特定設定的準則和採取適當的動作、 驗證呼叫端的身分識別和是否成功等傳遞訊息。因為它真的是自訂的處理機制實作任何擴充性應用程式需要。  
  
 若要使用 BizTalk Server 中的 WCF 自訂行為您會設定使用它**行為**Wcf-custom 或 Wcf-customisolated 配接器的接收位置或傳送埠 索引標籤。
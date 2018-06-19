---
title: 如何終止配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dfba2b61-b89f-41cd-a014-4e96daec6516
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd2621e15803dd5f6e8f449de530e84df1bc1b9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255990"
---
# <a name="how-to-terminate-an-adapter"></a>如何終止配接器
下列主題提供正確關閉配接器的指導。  
  
## <a name="terminating-an-adapter"></a>終止配接器  
 當傳訊引擎關閉時呼叫**IBTTransportControl**。**終止**上每個內含式配接器。 在這個方法傳回之後，BizTalk Server 就會將配接器終結。 對於原生配接器而言，這項作業會立即發生，但對於 Managed 配接器來說，這項作業的發生時間就比較不明確，這是因為 .NET 記憶體回收程序使然。 此配接器應該封鎖**Terminate**並且進行必要的清除工作，直到它已準備好終結。  
  
## <a name="terminating-isolated-receive-adapters"></a>終止外掛式接收配接器  
 外掛式接收配接器沒有**Terminate**上呼叫，因為它們不會裝載在 BizTalk 服務。 請改為呼叫**IBTTransportProxy**。**Ibttransportproxy**通知傳訊引擎它們即將關閉。  
  
## <a name="clean-up-com-objects-by-using-marshalreleasecomobject"></a>使用 Marshal.ReleaseComObject 清除 COM 物件  
 在寫入使用 COM 物件的 Managed 程式碼時，Common Language Runtime (CLR) 會產生 Proxy 物件以保存 COM 物件的參考。 Proxy 物件是 Managed 物件，受記憶體回收的一般規則管制。 當記憶體回收行程只看到 .NET 執行階段所配置的記憶體，而不知道有 COM 物件存在時，就會發生問題。 因為 Proxy 物件所佔空間很小，所以當 CLR 記憶體回收行程不知道有它的存在時，就可能導致記憶體中保留了所佔空間很大的 COM 物件。  
  
 若要避免這個問題，明確釋放基礎 COM 物件時，您已完成，特別是任何**IBTTransportBatch**物件。 您可以呼叫**封送處理**。**ReleaseComObject**。  
  
> [!NOTE]
>  **ReleaseComObject**傳回剩餘參考的數目，並只釋放 COM 物件，此傳回值為零。 通常**ReleaseComObject**稱為在迴圈中，以確保釋放物件。 完成之後，您應該呼叫**SuppressFinalize**此物件上因為沒有完成的項目。 最後一個步驟是檢查這是否真的是 COM 物件。  
  
 下列的程式碼顯示上述的程序：  
  
```  
if (Marshal.IsComObject (batch))  
(  
While (0 <Marshal.ReleaseComObject(batch)  
;  
GC.SuppressFinalize (batch);  
  
```  
  
 明確地釋放**IBTTransportBatch**從傳回的物件**Ibttransportproxy**可大幅提升效能。  
  
## <a name="always-use-terminate-when-closing-an-adapter"></a>在關閉配接器時永遠使用終止  
 將程式碼辨識為配接器的 BizTalk server，您必須實作介面呼叫**IBTTransportControl**。 這個介面會定義 BizTalk Server 如何與您的配接器進行通訊，且定義如下：  
  
```  
public interface IBTTransportControl   
{  
void Initialize(IBTTransportProxy transportProxy);  
void Terminate();  
}  
```  
  
 介面包含兩個方法：**初始化**和**Terminate**。  
  
### <a name="initialize"></a>[初始化]  
 BizTalk Server 會呼叫**初始化**方法之後載入配接器組件。 這麼做可以將傳輸 Proxy (BizTalk Server 的主控點) 傳遞至配接器。 實作**初始化**只會傳輸 proxy 儲存在成員變數中。  
  
### <a name="terminate"></a>Terminate  
 BizTalk Server 會呼叫**Terminate**方法在服務關閉，可讓配接器的時間完成所有批次的執行。 這可讓實作**Terminate**方法更能配合。  
  
 配接器都不會傳回**Terminate**它有任何暫止的工作完成之前呼叫。 當 BizTalk Server 呼叫**Terminate**，配接器應該嘗試停止所有目前的工作，不會啟動任何新的。  
  
 因為**Terminate**稱為服務關閉的一部分，服務控制管理員會結束處理序永久地封鎖配接器如果**Terminate**。 在這種情況下，服務控制管理員在停止 BizTalk Server 服務時會顯示警告訊息。 如有可能，請避免以這種方式永久地終止配接器。 如果配接器未正確地處理終止程序，而且在程序開始關閉時仍有執行緒在執行，則您可能會在關閉時偶爾看到發生 BizTalk Server 存取違規的情況。  
  
 因為這個 BizTalk Server 介面具有非同步的本質，所以在負載過低時可能會積存許多批次，因此造成仍有執行緒在執行中。 **Terminate**呼叫應該實作成等到配接器已順利在 BizTalk Server 上執行後再繼續每個批次結束時。 結束批次訊號是**BatchComplete**從 BizTalk Server 的回呼。 **Terminate**呼叫應該等候每個擱置**BatchComplete**發生。 不過，批次的執行必須成功才行。 也就是說，呼叫**IBTTransportBatch**::**完成**絕不能失敗。 如果呼叫**IBTTransportBatch**::**完成**失敗，沒有任何批次回呼。  
  
 在瞭解您必須對配接器新增同步化程式碼之後，實作就相當簡單。  
  
 其中一個簡單的方法為實作複合的同步化物件**輸入**和**保留**工作者執行緒的方法和**終止**方法時，該區塊執行緒目前仍在受保護的執行。 (附帶一提，解決方案是非常類似於熟悉的多個讀取器 / 單一寫入器結構所在的工作者執行緒可以視為讀取器和**終止**為寫入器的方法。)  
  
 **終止**方法如下所示：  
  
```  
void terminate ()  
{  
this.control.Terminate();  
}  
```  
  
 對於每個工作者執行緒：  
  
```  
If (!this.control.Enter())  
return; // we can’t enter because Terminate has been called  
try  
{  
//  create and fill batch  
batch.Done();  
}  
catch (Exception)  
{  
//  we are not expecting a callback  
This.control.Leave();  
}  
```  
  
 在來自 BizTalk Server 的回呼中：  
  
```  
batchComplete (…)  
{  
//  the callback from BizTalk Server  
//  process results  
this.control.Leave();  
}  
```  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在「基本配接器」範例中提供 ControlledTermination.cs 範例程式碼，顯示本文所述的同步化機制。
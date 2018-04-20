---
title: 配接器裝載模型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf9a8e6b-8c8d-47ec-b2a3-aed58206121d
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 645a1fcd41650c98c442549a898f7083be770842
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="adapter-hosting-model"></a>配接器裝載模型
BizTalk 配接器通常裝載 BizTalk 服務 Btsntsvc.exe 中。 這表示[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理配接器的存留期間。 不過也有某些情況 (說明如下) 是由其他處理序負責管理配接器。  
  
## <a name="in-process-adapters"></a>內含式配接器  
 配接器所管理的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]稱為內含式配接器。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會執行下列這些配接器：  
  
-   在啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時產生配接器  
  
-   在初始化期間將配接器的傳輸 Proxy 傳遞給配接器  
  
-   為配接器的要求提供服務  
  
-   在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 服務關閉時終止配接器  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會在執行階段將處理常式組態和端點組態資訊傳遞到配接器。 組態的其他部分則是用指定的，例如定義特定時間週期的服務視窗，在這些時間週期內，將會啟用配接器以主動處理要求。  
  
 BizTalk 服務可透過 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台或服務控制管理員，以手動方式關閉。 如果與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫的連線中斷，此服務便會自行回收。  
  
 在一般裝載模型中，接收端配接器和傳送端配接器都會連同傳訊引擎和協調流程引擎，裝載在與 BizTalk 服務相同的處理序中。 這種裝載模型十分彈性靈活，可以將接收、傳送和協調流程等主控件分開，也可以合併這些主控件。 在下圖中，主控件會在相同的處理序中執行這三項作業。  
  
 由於裝載模型的豐富多變，因此開發配接器時請務必牢記，傳送配接器和接收配接器可能永遠不會設定在相同的主控件中， 甚至可能設定成在不同的電腦上執行。  
  
 ![](../core/media/regularadapterhostingmodel.gif "RegularAdapterHostingModel")  
內含式配接器裝載模型  
  
## <a name="isolated-adapters"></a>外掛式配接器  
 在某些情況下，在 BizTalk 服務中裝載接收配接器並不可行。 例如，Internet Information Services (IIS) 程序模型是由 IIS 負責管理 ASP.NET 應用程式和 ISAPI 延伸模組。 BizTalk SOAP 配接器必須與 IIS 在相同的程序空間中執行，因而導致 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法控制任何 SOAP 配接器執行個體的存留期間。  
  
 這種類型的配接器，有另外一種適用的裝載模型，稱為外接式接收配接器，或簡稱為外接式配接器 (並沒有外接式傳送配接器的概念)。  
  
 因為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 不能建立外接式配接器，所以配接器必須取得其本身的傳輸 Proxy，並將自己登錄到該傳輸 Proxy 中。  
  
 下圖說明 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 裝載架構。 基於效能的考量，外接式主控件架構會嘗試排除任何非必要的處理序間通訊。 因為外接式配接器和 BizTalk 傳訊引擎位於相同的處理序，所以在配接器呼叫傳訊引擎時，並不會有任何處理序間的通訊。 在這種案例中，唯一也是無法避免的處理序間通訊發生在傳訊引擎和資料庫之間。  
  
 ![](../core/media/isolatedadapters.gif "IsolatedAdapters")  
外接式配接器裝載模型  
  
## <a name="see-also"></a>另請參閱  
 [何謂配接器架構？](../core/what-is-the-adapter-framework.md)
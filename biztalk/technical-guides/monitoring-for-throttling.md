---
title: 監視節流 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d1d4c72-6942-4572-b27f-c58d37c94062
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1dfbc767b5a5bc8f26625d0b5339221d8112d545
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997983"
---
# <a name="monitoring-for-throttling"></a>監視節流
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件會監視效能計數器，可表示的節流狀態[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 若要了解節流一些重要因素如下所示。  
  
- 根據速率的節流是每一部主機，並且根據訊息的傳輸速率輸入與輸出訊息。  
  
- 傳遞節流 」 的 (**MsgBox]-> [傳送埠或協調流程**)，輸入的速率會從 messagebox 接收訊息的速率。 輸出所處的訊息成功傳遞透過配接器的速率。  
  
- 發佈節流的 (**接收配接器**或是**協調流程]-> [MsgBox)，** 輸入的速度是從配接器接收的訊息和外送的速率是速率訊息插入 MsgBox。  
  
- 在資料庫中的郵件總數以外的主機之間，不存在任何節流的機制。  
  
  額外的背景資訊，請參閱主題[如何 BizTalk Server 實作主控件節流](http://go.microsoft.com/fwlink/?LinkID=155286)(<http://go.microsoft.com/fwlink/?LinkID=155286>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 整合了自我節流功能，可根據多個參數來協助防止伺服器負載過重。 導致節流發生的暫時負載過重並非重大的作業事件。 但是，在穩定的環境中不應該持續發生節流事件，這可能表示基礎結構層級有根本的問題。 管理組件能夠主動監視效能臨界值規則與這類持續節流狀況。  
  
  四個規則監視的使用情況/效能追蹤長期的節流設定下表所示，四個不同狀況所造成。  
  
|                                                     條件                                                     |                                        規則                                         |
|-------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
|     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 服務處理序記憶體     |     警告： BizTalk 針對節流，已高一段很長的處理序記憶體      |
|                                        正在處理的訊息數目                                         | 警告： BizTalk 節流，已在高內含式訊息計數一段很長 |
| 中的執行緒數目[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]程序 |      警告: BizTalk 針對高執行緒計數進行節流，已有一段很長的時間       |
|  大小[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫佇列   |      警告: BizTalk 針對高資料庫大小進行節流，已有一段很長的時間      |
  
 這些閾值規則會使用根據節流狀態指示器效能計數器的資料提供者。 如需有關這些效能計數器的詳細資訊，請參閱章節[效能計數器](http://go.microsoft.com/fwlink/?LinkId=157269)(<http://go.microsoft.com/fwlink/?LinkId=157269>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
 這些規則都設定為樣本數的平均值超過特定閾值時發出警示 （預設值為 30）。 比方說，「 警告： BizTalk 節流，已針對一段很長的高資料庫大小 」 是監視所有的節流狀態規則[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理程序在指定的電腦。 此規則會使用資料提供者根據節流狀態指示器效能計數器 」 biztalk： 訊息代理程式-高資料庫大小 」。 如果這個效能計數器的值是 1，則關聯的程序會因為高資料庫大小而進行節流。  
  
 前述規則被設定為 30 個取樣的平均值和取樣的平均值高於 0.6 時發出警示。 因為每個範例會在一分鐘的間隔內，這表示，在過去 30 分鐘，該電腦中的至少一個或多個 BizTalk Server 處理序進行節流因為高資料庫大小，60%的時間。  
  
 這個試誤可能不適合您的特定應用程式實例。 根據您的環境中的歷史行為，如之前所述，您應該設定這些規則的正確值透過下列方式：  
  
-   調整的範例。  
  
-   調整臨界值。  
  
-   如有必要，修改的提供者的取樣間隔。
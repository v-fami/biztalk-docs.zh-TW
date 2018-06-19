---
title: 設定 EPM 執行緒集區大小 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e170e76-5151-4306-9473-5b68e815219a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54afa88b51876d0ee56f548f263be1b00c37967a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271134"
---
# <a name="setting-the-epm-threadpool-size"></a>設定 EPM 執行緒集區大小
本主題將說明如何設定「結束點管理員」(EPM) 的執行緒集區大小。  
  
 在**進階**索引標籤中**主控件屬性**對話方塊中，沒有屬性，稱為**執行緒每一 CPU 的傳訊引擎數目上限**。 如需有關存取這個對話方塊中的指示，請參閱[如何建立新的主控件](../core/how-to-create-a-new-host.md)。 請使用此屬性來控制程序執行緒的集區大小，以便傳訊引擎用來處理訊息。 此屬性的預設值為 20，表示傳訊引擎最多只會在伺服器的每一個 CPU 上使用 20 個執行緒。  
  
 由於訊息批次會處理每個執行緒集區中，調整值**執行緒每一 CPU 的傳訊引擎數目上限**藉由變更伺服器上的資源使用率的 dynamics 可能會影響效能。 如需有關執行緒集區的運作方式的詳細資訊，請參閱[使用 「 BizTalk 傳訊引擎](../core/using-the-biztalk-messaging-engine.md)。  
  
 經測試顯示，在其中的 CPU 或 SQL Server 會過度使用的情況下，減少的值**執行緒每一 CPU 的傳訊引擎數目上限**可能會導致網路輸送量優勢。 例如，如果 MessageBox 資料庫伺服器顯示 CPU 的使用率超過 90%，或 SQL 鎖定等候時間攀升到 500-1000 毫秒以上，那麼減少集區中的執行緒數目，就可以降低對 SQL Server 進行連線的總次數，因此會提升訊息處理的效率。 在某些情況下，將最大執行緒集區大小設定成像是 2 這樣低的值，可以在輸送量方面帶來可觀的效益。  
  
## <a name="recommendation"></a>建議  
 當最佳化 BizTalk Server 安裝，建議您微調您的設定的值**執行緒每一 CPU 的傳訊引擎數目上限**。  當您嘗試降低 MessageBox 資料庫伺服器的使用率時，請考慮降低這個屬性的值。  
  
 當 BizTalk server 或 MessageBox 資料庫伺服器的使用率不高，並套用額外的負載不會導致更多的輸送量時，請嘗試增加的值**執行緒每一 CPU 的傳訊引擎數目上限**若要充分利用未使用的資源。  
  
## <a name="see-also"></a>另請參閱  
 [如何建立新的主機](../core/how-to-create-a-new-host.md)   
 [使用 「 BizTalk 傳訊引擎](../core/using-the-biztalk-messaging-engine.md)
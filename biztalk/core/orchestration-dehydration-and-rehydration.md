---
title: "協調流程凍結和解除凍結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57d7c0bf-a707-4ebd-afab-e75dd80c3c34
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7cee568cda6c869ede94e28bce441462c0c7cdc
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="orchestration-dehydration-and-rehydration"></a>協調流程凍結和解除凍結
當許多長時間執行的商務程序同時執行時，記憶體和效能是可能發生的問題。 協調流程引擎透過「凍結」和「解除凍結」協調流程執行個體來解決這些問題。  
  
 凍結是將協調流程狀態序列化到 SQL Server 資料庫中的程序。 解除凍結是此程序的反向︰ 還原序列化的協調流程從資料庫上次執行狀態。 凍結是藉由減少必須一次在記憶體中產生的協調流程數目，來將系統資源的使用降至最低。  
  
## <a name="dehydration"></a>Dehydration  
 協調流程引擎可能會判斷協調流程執行個體是否已經閒置相當長的一段時間。 它會計算閾值以決定各種動作發生之前應等待多久時間，若已超過這些閾值，則會凍結該執行個體。 這可能發生在下列情況下：  
  
-   當協調流程等待接收訊息，且等待時間超過引擎決定的閾值。  
  
-   當協調流程 「 接聽 」 的訊息，當您使用一樣 **接聽** 圖形與任何分支之前不會觸發引擎決定的閾值。 唯一的例外是當 **接聽** 圖形包含啟動接收。  
  
-   當協調流程中的延遲超過引擎決定的閾值。  
  
 引擎會儲存狀態以凍結執行個體，並釋出執行個體所需的記憶體。 透過凍結休眠的協調流程執行個體，引擎就可以讓大量的長時間執行之商務程序在相同電腦上同時執行。  
  
 您可以設定 12 個屬性，設定凍結在 BizTalk Server 中的運作方式。 本節中的主題會列出並說明屬性及其預設值，也會討論不同的值如何影響凍結的行為。  
  
## <a name="rehydration"></a>解除凍結  
 可透過訊息回條或在「延遲」圖形中指定的逾時過期來觸發協調流程引擎，以解除凍結協調流程執行個體。 然後，該引擎就會將已儲存的協調流程執行個體載入記憶體、還原其狀態，並從原本的停止點執行。 如需使用協調流程中的圖形的詳細資訊，請參閱[協調流程圖形](../core/orchestration-shapes.md)。  
  
 協調流程可設定為在一個以上的伺服器中執行。 在某個協調流程執行個體已經凍結之後，可以在這些伺服器中的任何一個將它解除凍結。 如果某個伺服器關閉，則引擎會在其他伺服器中，從它先前的狀態繼續執行協調流程。 引擎也會利用此功能，實作伺服器之間的負載平衡。  
  
## <a name="next-steps"></a>後續的步驟
  
-   [凍結預設屬性](../core/dehydration-default-properties.md)  
  
-   [如何計算凍結](../core/how-to-calculate-dehydration.md)  
  
-   [範例凍結計算](../core/sample-dehydration-calculation.md)  
  
-   [協調流程凍結效能計數器](../core/orchestration-dehydration-performance-counters.md)  
  
-   [BTSNTSvc.exe.config 檔案](../core/btsntsvc-exe-config-file.md)  
  
-   [可能影響凍結行為的其他活動](../core/other-activities-that-can-affect-dehydration-behavior.md)
---
title: "接收位置分解之後收到 Oracle 資料庫的變更通知 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22ad6da2-2979-4158-b1d1-d54095223af9
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f20fdcd30362a87a49be17d061a9fe86595c78c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receive-oracle-database-change-notifications-after-a-receive-location-breakdown"></a>接收位置分解之後收到 Oracle 資料庫的變更通知
假設您尚未 ACCOUNTACTIVITY 資料表進行變更時收到資料庫變更的通知訊息的 BizTalk 應用程式。 如果接收位置設定的一部分的 BizTalk 應用程式細分，同時新增到 ACCOUNTACTIVITY 資料表的記錄，將不會收到最近新增的記錄的通知。 您也不會知道接收位置再次可用時。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會公開繫結屬性， **NotifyOnListenerStart**，您可以設定要取得的接收位置已復原的通知。 您可以指定下列值**NotifyOnListenerStart**繫結屬性：  
  
-   將此屬性設定為**True**中接收通知，通知的接收位置的話，只要接收位置復原。  
  
-   將此屬性設定為**False**，而不會收到已復原的接收位置，接收位置復原後通知告知。  
  
 預設值是**True**。  
  
## <a name="configuring-the-oracle-database-adapter-behavior"></a>設定 Oracle 資料庫配接器行為  
 其中一個方法，您不需要執行任何特定的工作，產生中繼資料時，或在設定 BizTalk 應用程式時。 您只需要設定**NotifyOnListenerStart**繫結屬性據以 Wcf-oracledb 或 WCF 自訂接收位置。 若要建立 BizTalk 應用程式，您必須執行相同的一組工作中所述[接收 Oracle 資料庫變更通知以累加方式使用 BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-incrementally-using-biztalk-server.md)。 不過，設定 BizTalk 應用程式使用時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以嘗試的值變更**NotifyOnListenerStart**繫結屬性和查看兩個設定的差異。  
  
 下圖示範如何收到通知的值根據**NotifyOnListenerStart**繫結屬性。  
  
 ![設定通知的 SQL 配接器](../../adapters-and-accelerators/adapter-oracle-database/media/4018300a-1a58-47da-ac9d-c77c13d7081d.gif "4018300a-1a58-47da-ac9d-c77c13d7081d")  
  
 請注意，在第一個案例中，當**NotifyOnListenerStart**設**True**並記錄插入資料庫資料表向下接收位置時，配接器只會傳送給您接收位置出現時的通知訊息。 配接器不會執行任何作業可以處理的接收位置已關閉時插入記錄。 配接器用戶端必須實作相關的邏輯來處理的接收位置已關閉時插入記錄在應用程式中。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk Server 接收的 Oracle 資料庫變更通知](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-biztalk-server.md)
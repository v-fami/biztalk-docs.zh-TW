---
title: "如何避免磁碟 Contention1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b4f8e10-16b0-45f9-8787-da16266da980
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 702665046dbaee77412675e4be0edc602dd9e7e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-avoid-disk-contention"></a>如何避免磁碟爭用
BizTalk Server 設計為一個持續性的系統，因此在高輸送量的情況下，MessageBox 可能會遇到嚴重的爭用情況。 這個爭用情況可能會因緩慢的磁碟而加重。 如果磁碟緩慢 (磁碟閒置時間的百分比很低)，這可能會造成 SQL 鎖定更久 (高鎖定等候時間及高鎖定逾時)，使得 MessageBox 表格 (多工緩衝處理和應用程式佇列) 變大、讓資料庫膨脹，而節流最後會讓整體可持續的輸送量變低。  
  
 若要避免磁碟爭用情況，建議您執行下列作業：  
  
-   使用高速 (多磁針) 磁碟。  
  
-   可能的話，在高速 SAN 上部署資料庫。 如果有多個資料庫共用相同的磁碟，建議您在不同的專用磁碟上設定這些資料庫。 此外，也建議您將 MessageBox 資料庫的 MDF 和 LDF 檔案分開放到不同的磁碟上。  
  
-   如果 SQL 非常需要 CPU，請考慮將 MessageBox 資料庫分開放到與追蹤資料庫不同的專用伺服器上。  
  
-   設定好 MessageBox 資料庫專用的伺服器之後，請考慮升級 CPU 及/或新增更多的 CPU。 監視 SQL Server 的本機磁碟機，因為 MSDTC 記錄會儲存在本機磁碟機 (C:\WINDOWS\system32\Msdtc)。  
  
-   如果因為 PageFile 或 MSDTC 記錄的原因，而在本機磁碟機上造成爭用，請嘗試將 PageFile 及/或 MSDTC 記錄移到另一個磁碟機。
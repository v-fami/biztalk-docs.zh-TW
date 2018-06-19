---
title: 監視與降低 DTC 記錄檔磁碟 I/O 競爭 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f8b968dd-216e-454f-9224-aaf92ffd363b
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca71b55c2f9e18875ef67e840e8dac18a81dddac
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26007415"
---
# <a name="monitoring-and-reducing-dtc-log-file-disk-io-contention"></a>監視與降低 DTC 記錄檔的磁碟 I/O 競爭
分散式交易協調器 (DTC) 記錄檔可以成為在交易密集的環境中的磁碟 I/O 瓶頸。 使用支援交易，例如 SQL Server、 MSMQ 或 MQSeries，或在多個 MessageBox 的環境中的介面卡時，這是特別有用。 交易式配接器使用 DTC 交易，並多 MessageBox 環境會大量使用 DTC 交易。  
  
## <a name="monitoring-usage-in-clustered-and-non-clustered-environments"></a>監視叢集和非叢集環境中的使用方式  
 若要確保 DTC 記錄檔不會發生磁碟 I/O 瓶頸，您應監視磁碟 I/O 使用量 DTC 記錄檔所在的 SQL Server 資料庫伺服器上的磁碟。  
  
 在環境中，SQL Server 已叢集化，這是不太多的主要考量因為記錄檔，就會共用的磁碟機，可能會有多個磁針的快速 SAN 磁碟機上。 因為可能會成為瓶頸，以在非叢集環境或與其他需要大量的磁碟檔案的共用磁碟上的 DTC 記錄檔時，不過仍應監視磁碟 I/O 使用量。  
  
## <a name="troubleshooting-dtc"></a>疑難排解 DTC  
 如需疑難排解 DTC 的詳細資訊，請參閱 「 疑難排解問題與 MSDTC 」 中 BizTalk Server 說明在[http://go.microsoft.com/fwlink/?LinkId=153237](http://go.microsoft.com/fwlink/?LinkId=153237)。  
  
## <a name="see-also"></a>請參閱  
 [檢查清單：設定 Windows Server](../technical-guides/checklist-configuring-windows-server.md)
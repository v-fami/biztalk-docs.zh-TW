---
title: "監視與降低 DTC 記錄檔磁碟 I/O 競爭 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8b968dd-216e-454f-9224-aaf92ffd363b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca71b55c2f9e18875ef67e840e8dac18a81dddac
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="monitoring-and-reducing-dtc-log-file-disk-io-contention"></a><span data-ttu-id="ecb12-102">監視與降低 DTC 記錄檔的磁碟 I/O 競爭</span><span class="sxs-lookup"><span data-stu-id="ecb12-102">Monitoring and Reducing DTC Log File Disk I/O Contention</span></span>
<span data-ttu-id="ecb12-103">分散式交易協調器 (DTC) 記錄檔可以成為在交易密集的環境中的磁碟 I/O 瓶頸。</span><span class="sxs-lookup"><span data-stu-id="ecb12-103">The Distributed Transaction Coordinator (DTC) log file can become a disk I/O bottleneck in transaction-intensive environments.</span></span> <span data-ttu-id="ecb12-104">使用支援交易，例如 SQL Server、 MSMQ 或 MQSeries，或在多個 MessageBox 的環境中的介面卡時，這是特別有用。</span><span class="sxs-lookup"><span data-stu-id="ecb12-104">This is especially true when using adapters that support transactions, such as SQL Server, MSMQ, or MQSeries, or in a multi-MessageBox environment.</span></span> <span data-ttu-id="ecb12-105">交易式配接器使用 DTC 交易，並多 MessageBox 環境會大量使用 DTC 交易。</span><span class="sxs-lookup"><span data-stu-id="ecb12-105">Transactional adapters use DTC transactions, and multi-MessageBox environments make extensive use of DTC transactions.</span></span>  
  
## <a name="monitoring-usage-in-clustered-and-non-clustered-environments"></a><span data-ttu-id="ecb12-106">監視叢集和非叢集環境中的使用方式</span><span class="sxs-lookup"><span data-stu-id="ecb12-106">Monitoring Usage in Clustered and Non-Clustered Environments</span></span>  
 <span data-ttu-id="ecb12-107">若要確保 DTC 記錄檔不會發生磁碟 I/O 瓶頸，您應監視磁碟 I/O 使用量 DTC 記錄檔所在的 SQL Server 資料庫伺服器上的磁碟。</span><span class="sxs-lookup"><span data-stu-id="ecb12-107">To ensure that the DTC log file does not become a disk I/O bottleneck, you should monitor the disk I/O usage for the disk where the DTC log file resides on the SQL Server database server.</span></span>  
  
 <span data-ttu-id="ecb12-108">在環境中，SQL Server 已叢集化，這是不太多的主要考量因為記錄檔，就會共用的磁碟機，可能會有多個磁針的快速 SAN 磁碟機上。</span><span class="sxs-lookup"><span data-stu-id="ecb12-108">In an environment where SQL Server is clustered, this is not as much of a concern because the log file will already be on a shared drive, which will likely be a fast SAN drive with multiple spindles.</span></span> <span data-ttu-id="ecb12-109">因為可能會成為瓶頸，以在非叢集環境或與其他需要大量的磁碟檔案的共用磁碟上的 DTC 記錄檔時，不過仍應監視磁碟 I/O 使用量。</span><span class="sxs-lookup"><span data-stu-id="ecb12-109">You should nevertheless still monitor the disk I/O usage since it can become a bottleneck in non-clustered environments or when the DTC log file is on a shared disk with other disk-intensive files.</span></span>  
  
## <a name="troubleshooting-dtc"></a><span data-ttu-id="ecb12-110">疑難排解 DTC</span><span class="sxs-lookup"><span data-stu-id="ecb12-110">Troubleshooting DTC</span></span>  
 <span data-ttu-id="ecb12-111">如需疑難排解 DTC 的詳細資訊，請參閱 「 疑難排解問題與 MSDTC 」 中 BizTalk Server 說明在[http://go.microsoft.com/fwlink/?LinkId=153237](http://go.microsoft.com/fwlink/?LinkId=153237)。</span><span class="sxs-lookup"><span data-stu-id="ecb12-111">For information about troubleshooting DTC, see "Troubleshooting Problems with MSDTC" in BizTalk Server Help at [http://go.microsoft.com/fwlink/?LinkId=153237](http://go.microsoft.com/fwlink/?LinkId=153237).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecb12-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="ecb12-112">See Also</span></span>  
 [<span data-ttu-id="ecb12-113">檢查清單：設定 Windows Server</span><span class="sxs-lookup"><span data-stu-id="ecb12-113">Checklist: Configuring Windows Server</span></span>](../technical-guides/checklist-configuring-windows-server.md)
---
title: 交易式訊息批次 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b1790c05-e3f7-4667-8a9e-f6f208e55e40
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28be423aa500ba8950b5b2100ce68dba7743bd79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279526"
---
# <a name="transactional-message-batches"></a>交易式訊息批次
某些配接器必須協調外部交易與內部 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 交易。 例如，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供的 SQL 配接器必須協調 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 交易與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 交易。 若要這樣做，此配接器必須存取 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 交易物件。 將批次提交給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之前，要明確建立交易物件並讓它與此批次產生關聯。 具有關聯交易物件的批次稱為交易式批次。 您可以藉由提供您自己的 Microsoft Distributed Transaction Coordinator (MSDTC) 交易物件，與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之間達成「只有一次保證」的資料往來傳遞。  
  
 由於批次中使用單一交易，所以類似 SQL 配接器的交易式資料庫配接器在外部資料庫中可能會有死結。 這就是將 SQL 配接器的批次大小以硬式編碼方式編寫成一的原因。  
  
 萬一配接器需要在該交易範圍內登錄其他資源管理員 (如另一個資料庫或 MSMQ) 時，它必須建立明確外部交易，並將此交易傳遞給傳訊引擎。 建立外部交易並讓它與批次產生關聯稱為交易式批次。 交易式配接器是透過明確建立外部 Microsoft Distributed Transaction Coordinator (MSDTC) 交易來利用交易式批次的配接器。  
  
 配接器為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供交易的其中一個原因，是要確保 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 或外部系統具有資料的記錄。 這項記錄可確保此訊息只會傳遞一次。  
  
> [!NOTE]
>  如需 MSDTC 的詳細資訊，請參閱在分散式交易協調器文件： [http://go.microsoft.com/fwlink/?LinkId=44297](http://go.microsoft.com/fwlink/?LinkId=44297)。  
  
 檔案配接器是不需要存取交易的一個配接器範例，因為它所管理的外部檔案作業不是交易式。 在此情況下，此配接器不會提供交易物件給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 另一方面，SQL 配接器會與 SQL 資料庫互動，而且在它的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 訊息互動之外可能會有其他的作業。 在此情況下，此配接器將外部 MSDTC 交易傳遞給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可能是一件合理的事情。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [處理交易](../core/handling-transactions.md)
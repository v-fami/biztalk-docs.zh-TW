---
title: 範例架構的小型&amp;中型公司 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, examples
ms.assetid: fc8c2fdd-bcb1-481c-b351-03092dd48540
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fa7911b7b2da942d559f2c85ad32e896c79d174
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sample-architectures-for-small-amp-medium-sized-companies"></a>範例架構的小型&amp;中型公司
本節提供您要協助保護小型或中型公司資產安全時部署 Microsoft BizTalk Server 的範例架構。 雖然這些架構鼓勵使用深層防禦與服務分隔使攻擊的影響降至最低，但它們假設的硬體、軟體與人力資源的數量是大型公司一般才有的數量。  
  
 不過，小型與中型公司 (或擁有小型 BizTalk Server 部署的大型公司) 應該也關心如何保護其環境。 在查看過公司如何部署或規劃部署其 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 方案之後，我們衍生出中小型公司的範例架構，以便平衡可用資源與可能的最大安全性。 您應該使用本節中的資訊，協助規劃您自己的部署。 評估您的商務需求與資產之後，您可能決定對 BizTalk Server 部署使用不同的架構。  
  
 為了易於查看架構的外觀，本節根據您可能在環境中使用的各種配接器提供範例架構。 這些圖會顯示哪些拓樸元件與配接器無關，以及哪些元件與您在 BizTalk Server 環境中使用的配接器有關。  
  
 我們也會根據您可搭配 BizTalk Server 使用的一些配接器來檢查使用實例。 為了協助您規劃和設計自己的架構，我們提供此範例架構的威脅模型分析。 此分析視您用來與夥伴通訊的配接器而定，提供您對可能影響公司的潛在安全性問題更深入的觀察。  
  
 雖然本節提供協助您設計 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安全部署的資訊，但若要增加環境的安全性，您還要考慮在環境中保護各伺服器之間的通訊安全。  
  
> [!IMPORTANT]
>  本節假設您不使用「商務活動監控」(BAM)。 此功能需要額外考量安全性。 討論這[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。  
  
> [!NOTE]
>  如需配接器不在本文件中描述的詳細資訊，請參閱 BizTalk Server 開發人員中心 ([http://go.microsoft.com/fwlink/?LinkId=46420](http://go.microsoft.com/fwlink/?LinkId=46420)。)  
  
## <a name="in-this-section"></a>本節內容  
  
-   [範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)  
  
-   [範例架構： HTTP 和 SOAP 配接器](../core/sample-architecture-http-and-soap-adapters.md)  
  
-   [範例架構： BizTalk 訊息佇列](../core/sample-architecture-biztalk-message-queuing.md)  
  
-   [範例架構： FTP 配接器](../core/sample-architecture-ftp-adapter.md)  
  
-   [範例架構： File 配接器](../core/sample-architecture-file-adapter.md)
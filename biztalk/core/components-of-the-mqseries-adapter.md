---
title: MQSeries 配接器的元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, BizTalk component
- MQSeries adapters, components
- MQSeries components, MQSeries adapters
- BizTalk components
- MQSeries adapters, MQSeries component
ms.assetid: 923974cb-371d-47dc-99a7-2f7b93f60ada
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58726b6528af55da6554ff740208b3e03bdc806e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232510"
---
# <a name="components-of-the-mqseries-adapter"></a>MQSeries 配接器的元件
MQSeries 配接器會使用兩個元件，協助 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 與 MQSeries Server for Windows 之間的文件轉換。  
  
-   **BizTalk 元件。** Microsoft 在同一部電腦上安裝此元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 此元件會與 BizTalk Server 通訊。  
  
-   **MQSeries 元件。** 在 MQSeries Server for Windows 上安裝此元件。 MQSeries Server for Windows 上執行[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]。 此元件 (稱為 MQSAgent) 會與 IBM MQSeries Server 通訊。  
  
    > [!NOTE]
    >  MQSeries 配接器的 MQSAgent 元件支援在 Windows 上，根據 MQSeries Server 5.3、CSD10 或更新版，以及 WebSphere MQSeries Server 6.0 來執行。  
  
 下圖概述配接器的一般用法。  
  
 ![文件 MQSeries Server 與 BizTalk 之間流量](../core/media/bts-dev-mqadapterflow.gif "BTS_Dev_MQAdapterFlow")  
  
 MQSeries 配接器是一種連線解決方案，可讓您在企業中使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 及 MQSeries 作為選擇的傳訊標準。 開發此解決方案的動機有部分是來自下列問題：  
  
-   配合客戶對於簡單安裝和組態及 MQSeries 連線解決方案的要求。  
  
-   支援最大可達 100 MB 大小的訊息  
  
-   提供 MQSeries 支援  
  
-   為傳送到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 MQSeries 訊息提供隨插即用的連線解決方案  
  
 MQSeries 配接器是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組合軟體之接收服務的主要新增功能，它為各種通訊協定標準提供一組待命程式。 待命程式會將通訊協定 (例如 HTTP、FTP 或 MQSeries) 連接到企業應用程式整合 (EAI)、B2B，或是應用程式對應用程式整合的交易關係。  
  
## <a name="see-also"></a>另請參閱  
 [MQSeries 配接器架構](../core/mqseries-adapter-architecture.md)   
 [何謂 MQSeries 配接器？](../core/what-is-the-mqseries-adapter.md)
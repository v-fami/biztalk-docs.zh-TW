---
title: "管理 MessageBox 資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [MessageBox database], about managing MessageBox database
- managing [MessageBox database]
- MessageBox database, managing
ms.assetid: 9675b5d5-7a69-468d-be42-34a72cd6e5c2
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e854ad0f7014de8241f8a7b6af6addd49cb4da5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="managing-messagebox-databases"></a>管理 MessageBox 資料庫
MessageBox 資料庫有三個基本功能。 它儲存訂閱與追蹤資訊，並將訊息傳遞到符合訂閱的服務。 MessageBox 資料庫是一個主控件平台，儲存每個 BizTalk 主控件的佇列和狀態資料表。 MessageBox 資料庫也儲存訊息及訊息屬性。  
  
 若 MessageBox 資料庫是環境中具有洩露風險的資產，建議您使用網際網路通訊協定安全性 (IPSec) 或安全通訊端層 (SSL) 來限制與保護往返 MessageBox 資料庫的通訊。  
  
 若您使用 Windows Server 2003，您必須在 MessageBox 資料庫上啟用分散式交易協調器 (DTC)。 您也必須啟用多部電腦部署的網路用戶端。 如需詳細資訊，請參閱[管理伺服器的連接埠](../core/ports-for-the-administration-server.md)。  
  
 本節包含有關在您的環境中管理 MessageBox 資料庫的程序資訊。 如需 MessageBox 資料庫和訂用帳戶的概念資訊模型 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]用來處理訊息，請參閱[MessageBox 資料庫](../core/the-messagebox-database.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何新增新的 MessageBox 資料庫](../core/how-to-add-a-new-messagebox-database.md)  
  
-   [如何停用新訊息發佈](../core/how-to-disable-new-message-publication.md)  
  
-   [如何刪除 MessageBox 資料庫](../core/how-to-delete-a-messagebox-database.md)
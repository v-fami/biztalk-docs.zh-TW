---
title: "在匯入管理組件之前 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e3c13dd-613a-4885-a5d2-ad3ee492ff25
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c11849c379a4654bed78a8e86ba263e6da428c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="before-you-import-the-management-pack"></a>匯入管理組件之前
最佳做法，您應該匯入 Windows Server 管理組件，您要使用的作業系統。 在匯入之前[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件，採取下列動作：  
  
-   確定已安裝 Operations Manager 2007 R2/2012年。  
  
-   您必須是 SCOM Administrators 群組或 SCOM 作者群組的成員。 SCOM 管理伺服器上的本機管理員具有所有權利及權限授與給 SCOM Administrators 群組。  
  
-   設定 BizTalk Server 為 Operations Manager 中的受管理電腦上您想要管理每個 BizTalk Server 的 SCOM 代理程式的部署。 SCOM 代理程式部署涉及下列工作：  
  
    -   安裝 SCOM 代理程式。  
  
    -   建立 BizTalk SCOM 代理程式帳戶。  
  
    -   設定**執行身分**帳戶。 將執行身分帳戶加入至下列群組：  
  
        -   BizTalk 群組。  
  
        -   BizTalk 系統管理員。  
  
        -   SSO 系統管理員。  
  
        -   SSO 分支機構系統管理員。  
  
    -   開始監視。  
  
-   在 Operation Manager 主控台中，受管理的電腦處於狀況良好。  
  
-   設定已設定，例如任何所需的執行身分帳戶或設定檔的任何使用者帳戶。 此管理組件包含執行身分設定檔名為 「 BizTalk Server 監視帳戶 」 和 「 BizTalk Server 探索帳戶 」 來定義每個代理程式為基礎的特定認證。 您可能要在匯入管理組件之後，某些代理程式使用此執行身分設定檔。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [此管理組件中的檔案](../technical-guides/files-in-this-management-pack.md)  
  
-   [建議的其他管理組件](../technical-guides/recommended-additional-management-packs.md)
---
title: 如何在多重電腦實例中設定 SSO |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, SSO
- SSO database, clustering
- clustering, Master Secret server
- SSO, configuring
- configuring, Master Secret server
- Master Secret server, clustering
- clustering, SSO database
- Master Secret server, configuring
- SSO, multiple computers
ms.assetid: 4511a03d-96f2-45f0-9891-e8b3e253499c
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45bfa58c1fc11a76109f56938b8e1b43790935f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248750"
---
# <a name="how-to-configure-sso-in-a-multicomputer-scenario"></a>如何在多重電腦實例中設定 SSO
本節包含在三部電腦實例中設定「企業單一登入」(SSO) 的指示。  
  
 在下列實例中，電腦 A 是主要密碼伺服器，電腦 B 是「單一登入」伺服器，而電腦 C 則保存 SSO 資料庫。 電腦 B 可做為執行階段伺服器、管理伺服器 (SSO 的管理子服務使用此伺服器以管理 SSO 資料庫) 或對應伺服器 (SSO 的管理與用戶端子服務使用此伺服器以管理對應)。  
  
 若您要在環境中新增更多 SSO 伺服器，請遵循設定電腦 B 的步驟。任何新的 SSO 伺服器都將指向現有的 SSO 資料庫，而且不可以做為主要密碼伺服器。  
  
> [!NOTE]
>  建議您在與「單一登入」伺服器和 SSO 資料庫不同的電腦上設定主要密碼伺服器。  
  
### <a name="to-configure-the-master-secret-server-and-create-the-sso-database-on-computer-a"></a>若要在電腦 A 設定主要密碼伺服器並建立 SSO 資料庫  
  
1.  執行 BizTalk Server 自訂安裝，而且只安裝「企業單一登入主要密碼伺服器」元件。  
  
2.  執行 [組態精靈]，在主要密碼伺服器上設定 SSO。 在**組態問題**頁面上，選取選項以**建立新的 SSO 系統**。  
  
3.  在**Windows 帳戶**頁面上，指定 SSO 服務的服務帳戶認證。 這必須是 SSO 系統管理員群組的成員。  
  
4.  在**資料庫組態**頁面上，指定 SQL Server （電腦 C） 的位置以及 SSO 資料庫 (SSODB) 的名稱。  
  
5.  指定選項以備份主要密碼。  
  
6.  完成組態。  
  
### <a name="to-configure-the-sso-server-on-computer-b"></a>在電腦 B 設定 SSO 伺服器  
  
1.  在電腦 B 上安裝「企業單一登入」。  
  
    > [!NOTE]
    >  這可以是 BizTalk Server 或 Host Integration Server 電腦、Web 伺服器或僅限 SSO 伺服器 (SSO 執行階段元件)。  
  
2.  執行 [組態精靈] 以設定 SSO。 在**組態問題**頁面上，選取選項以**加入現有的 SSO 系統**。  
  
3.  在**Windows 帳戶**頁面上，指定 SSO 服務的服務帳戶認證。 這必須是 SSO 系統管理員群組的成員。  
  
4.  在**資料庫組態**頁面上，指向 SQL Server （電腦 C） 的位置以及 SSO 資料庫 (SSODB) 的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [如何叢集化主要密碼伺服器](../core/how-to-cluster-the-master-secret-server1.md)   
 [安裝 SSO](../core/installing-sso.md)
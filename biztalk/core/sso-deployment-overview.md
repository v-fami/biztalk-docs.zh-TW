---
title: SSO 部署概觀 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSO, deploying example
- SSO, deploying
- deploying, SSO
- SSO, multiple computers
- examples, deploying
ms.assetid: 6eccee26-c392-41fe-97fb-3afe1685540f
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c98a12c11ae735945f4e69631e7211c05c0b9186
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022364"
---
# <a name="sso-deployment-overview"></a>SSO 部署概觀
此範例中的系統是部署在包含下列電腦的三個網域中：  
  
 **網域 ORCH.com**  
  
- ORCH 網域控制站  
  
- HIS1、HISSO 伺服器  
  
- HIS2、主要密碼伺服器  
  
- HIS3、管理資料庫  
  
  **網域 SQL.com**  
  
- SQL 網域控制站  
  
- SQL2、SSO 資料庫  
  
  **網域 HIS.com**  
  
- HIS 網域控制站  
  
- HIS4 資料庫  
  
  定義此部署的重點如下：  
  
- 網域 ORCH.com 和網域 SQL.com 有一個雙向選擇性信任關係。  
  
- 網域 ORCH.com 設定成原生 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 或 [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] 功能等級。  
  
- 所有 SSO 服務都是在 ORCH.com 網域使用者帳戶執行 (Orch\SSOSvcUser)。 使用者設定成擁有 SQL.com 網域中 SQL2 機器的存取權限。 會為 ORCH.com 網域中的通訊協定轉換和限制委派設定使用者。  
  
- 會為執行測試程式而設定其他 ORCH.com 網域使用者 (Orch\TestAppUser)。 也會為通訊協定轉換和限制委派設定此使用者。  
  
## <a name="see-also"></a>另請參閱  
 [部署程序](../core/deployment-process.md)
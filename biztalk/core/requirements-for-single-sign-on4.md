---
title: TIBCO EMS 配接器的 SSO 需求 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 645c7b3f-f860-4c20-b5ca-a8fb93736344
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8baf665a7f997293130a2c1eb93f893167f39a4f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967879"
---
# <a name="requirements-for-single-sign-on"></a>單一登入的需求

## <a name="overview"></a>概觀
Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) 提供單一登入 (SSO) 支援。 企業單一登入工具建立的分支機構應用程式代表一個伺服器系統 (例如 TIBCO EMS)。  
  
 若要使用「單一登入」，您需要：  
  
- Microsoft BizTalk Server
  
- Visual Studio  
  
- 企業單一登入  
  
- 支援 SSO 的伺服器系統  
  
  外掛式主控件應設定為信任的驗證
  
## <a name="enable-sso"></a>啟用 SSO  
  
1.  在 **傳輸屬性**視窗中，選取**是**for**使用 SSO**。  
  
2.  指定傳輸屬性時，選取適當的分支機構應用程式。  
  
     如需有關如何建立分支機構應用程式的資訊，請參閱 <<c0> [ 建立分支機構應用程式](../core/creating-affiliate-applications5.md)。  
  
    > [!NOTE]
    >  執行工作之後使用 SSO，請務必重設任何 Web 共用的資料夾，以**不會共用**。 不使用該資料夾的應用程式將會更新，或如果資料夾已共用，因為它會被視為使用中正確地解除安裝。  
  
## <a name="see-also"></a>另請參閱  
[保護配接器](../core/security-in-biztalk-adapter-for-tibco-ems.md)
---
title: TIBCO 會合配接器的 SSO 需求 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7d5c406b-f548-4df0-8644-fdf6a812a989
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e61b456def74ee76d887fa42149ee95b9ca3cbf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013735"
---
# <a name="requirements-for-single-sign-on"></a>單一登入的需求

## <a name="prerequisites"></a>必要條件
若要使用「單一登入」(SSO)，您必須具有下列項目：  
  
-   Microsoft BizTalk Server
  
-   Visual Studio  
  
-   企業單一登入  
  
-   支援 SSO 的伺服器系統  
  
-   外掛式主控件應設定為信任的驗證。  
  
## <a name="enable-sso"></a>啟用 SSO  
  
1. 在 **傳輸屬性**視窗中，選取**是**for**使用 SSO**。  
  
2. 指定傳輸屬性時，選取適當的分支機構應用程式。  
  
   如需詳細資訊，請參閱 <<c0> [ 建立分支機構應用程式](../core/creating-affiliate-applications1.md)。  
  
> [!NOTE]
>  執行工作之後使用 SSO，請務必重設任何 Web 共用的資料夾，以**不會共用**。 不使用該資料夾的應用程式將會更新，或如果資料夾已共用，因為它會被視為使用中正確地解除安裝。  
  
## <a name="see-also"></a>另請參閱  
[Security](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md)
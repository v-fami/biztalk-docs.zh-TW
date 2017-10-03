---
title: "如何移除 SSO |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Master Secret server, deleting
- SSO, deleting
- deleting, SSO
- deleting, Master Secret server
ms.assetid: 0e1ad8e3-0938-4f36-b85b-4631d0eeb8c9
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7134186161c3c0647a20047afcbbe317fcbad1ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-sso"></a>如何移除 SSO
若您移除 BizTalk Server，就不會再設定「企業單一登入」(SSO)，除非相依產品正在使用它。 但不會將它移除。 您必須個別移除 SSO。 您也可以還原組態資訊 (包括主要密碼)，以重複使用現有的資料。 如需詳細資訊，請參閱[如何還原主要密碼](../core/how-to-restore-the-master-secret.md)。  
  
### <a name="to-remove-enterprise-single-sign-on"></a>若要移除企業單一登入  
  
1.  備份主要密碼金鑰。 如需詳細資訊，請參閱[如何重新設定主要密碼](../core/how-to-back-up-the-master-secret.md)。  
  
2.  解除安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
3.  在 **[開始]** 功能表上，按一下 **[控制台]**。  
  
4.  按一下**新增/移除程式**。  
  
5.  在**新增/移除程式**對話方塊中，按一下  **Microsoft 企業單一登入**，然後按一下 **移除**。  
  
6.  按一下**是**當系統提示您確認移除的 Microsoft 企業單一登入。  
  
    > [!NOTE]
    >  如果您已安裝 BizTalk Server 執行階段、程式開發或管理功能，或是安裝了 Host Integration Server 管理功能，則在移除所有相依性之前，您將無法解除安裝「SSO 執行階段」或「管理」元件。  
  
## <a name="see-also"></a>另請參閱  
 [安裝 SSO](../core/installing-sso.md)
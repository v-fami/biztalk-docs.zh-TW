---
title: 如何設定 SSO 伺服器使用用戶端公用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications [SSO], selecting servers
- managing [SSO applications], selecting servers
- SSOClient [SSO], selecting servers
ms.assetid: a0f1038c-60c9-4e9d-a730-1ecfa036743b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f212bb5e6601274a473c6f9854d5e23af9715cd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008863"
---
# <a name="how-to-set-the-sso-server-using-the-client-utility"></a>如何設定和使用用戶端公用程式的 SSO 伺服器
每次使用 ssoclient 時，您必須先將使用者指向包含其組態資訊的正確「單一登入」伺服器。  
  
### <a name="to-set-the-sso-server-for-a-user-using-the-client-utility"></a>使用用戶端公用程式設定使用者的 SSO 伺服器  
  
1. 在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。  
  
2. 在命令列，移至「企業單一登入」安裝目錄。 預設的安裝目錄*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3. 型別<strong>ssoclient – 伺服器*\<單一登入伺服器\></strong><em>，其中\<</em>單一登入伺服器\>* 是連接到要單一登入伺服器的使用者名稱。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 分支機構應用程式](../core/sso-affiliate-applications.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)
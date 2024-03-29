---
title: 如何安裝密碼同步化 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing, Password Synchronization [SSO]
- Password Synchronization [SSO], installing
ms.assetid: 8ace0401-b759-4ea3-91a0-be2aa8b5a5a4
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1cd2db294ae0bd9e32db1a81209fe9226512e2a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996207"
---
# <a name="how-to-install-password-synchronization"></a>如何安裝密碼同步化
如同其他「單一登入」功能，預設的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝中不會安裝「密碼同步」，而且必須在安裝時特別選取。  
  
### <a name="to-install-password-synchronization"></a>安裝密碼同步  
  
1. 在 BizTalk Server CD 上瀏覽 **\<CDRoot\>\Platforms\SSO**資料夾。  
  
2. 執行**setup.exe**並遵循精靈中的指示。  
  
3. 選取 **密碼同步化**功能，並繼續進行安裝。  
  
   除此之外，您還需要透過密碼同步配接器來傳送及接收外部系統的密碼變更。 本節中的主題描述如何設定您自己的配接器。  
  
   您也可以連絡支援別名，以取得有關可用密碼同步配接器的資訊。  
  
   最後，若要擷取 Active Directory 中所做的密碼變更，除了安裝 ENTSSO 密碼同步功能以外，還需要在網域控制站上安裝元件來擷取密碼變更。  
  
   在將要從中擷取密碼的所有網域控制器上，必須安裝 Windows 密碼擷取元件和密碼變更通知服務 (PCNS，Password Change Notification Service)。 您可從下列位置安裝這些元件：  
  
   [http://go.microsoft.com/fwlink/?LinkId=68145](http://go.microsoft.com/fwlink/?LinkId=68145)  
  
   在網域控制站上繼續執行安裝之前，請先詳閱隨附文件 (也在此資料夾中)。  
  
## <a name="see-also"></a>另請參閱  
 [密碼同步](../core/password-synchronization2.md)
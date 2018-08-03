---
title: 如何產生主要祕密 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Master Secret server, generating
- managing [Master Secret server], generating
ms.assetid: 5512a8ee-bc5b-4fe4-90c7-41e3baaa723b
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41e7f000dbb53a054259ba18f5c1d118531c8138
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978335"
---
# <a name="how-to-generate-the-master-secret"></a>如何產生主要密碼
您必須具有主要密碼伺服器的管理權限，才可以執行此工作。 此外，您必須從主要密碼伺服器執行此工作。  
  
 您安裝「企業單一登入」的第一台伺服器會變成主要密碼伺服器。  
  
> [!IMPORTANT]
>  SSO 系統中只能有一台主要密碼伺服器。  
> 
> [!NOTE]
>  當「企業單一登入」是安裝為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝的一部分時，則會由組態精靈產生主要密碼。 若您想要產生新的主要密碼，只需執行此工作即可。  
  
### <a name="to-generate-the-master-secret-using-the-mmc-snap-in"></a>使用 MMC 嵌入式管理單元產生主要密碼  
  
1.  在 **[開始]** 功能表上，依序按一下 **[所有程式]** 及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  以滑鼠右鍵按一下**系統**，然後按一下**產生祕密**。  
  
### <a name="to-generate-the-master-secret-using-the-command-line"></a>使用命令列產生主要密碼  
  
1.  在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設的安裝目錄*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssoconfig-generateSecret \<*備份檔案*\>**，其中\<*備份檔案*\>的名稱包含主要密碼的檔案。  
  
     系統會提示您輸入密碼，以保護剛建立的檔案。  
  
    > [!NOTE]
    >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
## <a name="see-also"></a>另請參閱  
 [如何備份主要密碼](../core/how-to-back-up-the-master-secret.md)   
 [主要密碼伺服器](../core/master-secret-server.md)   
 [管理主要密碼](../core/managing-the-master-secret.md)
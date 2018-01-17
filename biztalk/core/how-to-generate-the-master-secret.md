---
title: "如何產生主要密碼 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Master Secret server, generating
- managing [Master Secret server], generating
ms.assetid: 5512a8ee-bc5b-4fe4-90c7-41e3baaa723b
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1a7ee4f8ffe73a71e8c0b2e3d45c7a966669fd8
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-generate-the-master-secret"></a>如何產生主要密碼
您必須具有主要密碼伺服器的管理權限，才可以執行此工作。 此外，您必須從主要密碼伺服器執行此工作。  
  
 您安裝「企業單一登入」的第一台伺服器會變成主要密碼伺服器。  
  
> [!IMPORTANT]
>  SSO 系統中只能有一台主要密碼伺服器。  
  
> [!NOTE]
>  當「企業單一登入」是安裝為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝的一部分時，則會由組態精靈產生主要密碼。 若您想要產生新的主要密碼，只需執行此工作即可。  
  
### <a name="to-generate-the-master-secret-using-the-mmc-snap-in"></a>使用 MMC 嵌入式管理單元產生主要密碼  
  
1.  在 **[開始]** 功能表上，依序按一下 **[所有程式]**及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  以滑鼠右鍵按一下 **系統**, ，然後按一下  **產生密碼**。  
  
### <a name="to-generate-the-master-secret-using-the-command-line"></a>使用命令列產生主要密碼  
  
1.  在 **啟動** ] 功能表上，按一下 [ **執行**, ，然後輸入 **cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssoconfig – generateSecret \<*備份檔案*\>**，其中\<*備份檔案*\>的名稱包含主要密碼的檔案。  
  
     系統會提示您輸入密碼，以保護剛建立的檔案。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>另請參閱  
 [如何備份主要密碼](../core/how-to-back-up-the-master-secret.md)   
 [主要密碼伺服器](../core/master-secret-server.md)   
 [管理主要密碼](../core/managing-the-master-secret.md)
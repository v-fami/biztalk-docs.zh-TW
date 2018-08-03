---
title: 如何啟用 SSO |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications [SSO], creating
- SSO, enabling
- maps [SSO], creating
- managing [SSO], enabling
- SSO, maps
- SSO, applications
- creating, applications [SSO]
- managing [SSO], creating affiliate applications
ms.assetid: dda89d15-6b70-4c40-b658-2f6cbdd545c8
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6bb2c6e5349a74fb212bdf7011fb294cb1810e67
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966255"
---
# <a name="how-to-enable-sso"></a>如何啟用 SSO
使用 MMC 嵌入式管理單元或命令列，可以啟用整個企業單一登入 (SSO) 系統。  
  
 執行啟用命令時，在短暫延遲之後才會啟用所有單一登入伺服器，因為每個伺服器都會輪詢 SSO 資料庫以獲得最新的全域資訊。  
  
 若您要設定 SSO 系統中的分支機構應用程式與對應，則還需建立分支機構應用程式。 在 SSO 分支機構系統管理員建立分支機構應用程式之後，應用程式系統管理員可將它變更，而應用程式使用者 (一般使用者) 可建立他們自己的對應。 如需詳細資訊，請參閱 <<c0> [ 管理分支機構應用程式](../core/managing-affiliate-applications.md)並[管理使用者對應](../core/managing-user-mappings.md)。  
  
### <a name="to-enable-the-sso-system-using-the-mmc-snap-in"></a>若要啟用使用 MMC 嵌入式管理單元的 SSO 系統  
  
1.  按一下 **開始**，按一下**所有程式**，按一下  **Microsoft 企業單一登入**，然後按一下**SSO 管理**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  以滑鼠右鍵按一下**系統**，然後按一下**啟用**。  
  
### <a name="to-enable-the-sso-system-using-the-command-line"></a>使用命令列啟用 SSO 系統  
  
1.  依序按一下 **[開始]** 及 **[執行]**，然後輸入 **cmd**。  
  
2.  在命令列提示字元中，移至「企業單一登入」安裝目錄。 預設的安裝目錄**\<磁碟機\>**: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssomanage – enablesso**。  
  
    > [!NOTE]
    >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
### <a name="to-enable-sso-to-create-affiliate-applications-and-mappings"></a>啟用 SSO 以建立分支機構應用程式與對應  
  
1. 以 SSO 系統管理員或 SSO 分支機構系統管理員身分登入 SSO 伺服器，或在擁有 SSO 的 SSO 管理子服務的電腦上登入。  
  
2. 在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。  
  
3. 在命令列提示字元中，移至「企業單一登入」安裝目錄。 預設的安裝目錄*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4. 型別**ssomanage-enablesso**啟用企業單一登入服務。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
5. 以 SSO 分支機構系統管理員身分登入。  
  
6. 型別**ssomanage-createapps *\<應用程式檔案\>*** 建立分支機構應用程式，其中\<應用程式檔案\>是 XML 檔案其中包含定義分支機構應用程式。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 SSO 伺服器](../core/how-to-set-the-sso-server.md)   
 [如何停用 SSO](../core/how-to-disable-sso.md)   
 [如何更新 SSO 資料庫](../core/how-to-update-the-sso-database.md)   
 [使用 SSO](../core/using-sso.md)
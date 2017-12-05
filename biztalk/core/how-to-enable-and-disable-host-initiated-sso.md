---
title: "如何啟用和停用主控件初始化的 SSO |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- host initiated SSO, disabling
- disabling, host initiated SSO
- enabling, host initiated SSO
- host initiated SSO, enabling
ms.assetid: a11d314a-6ff9-4d0a-89c3-c412541c2cec
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1e5783893bbc9091d0a5f1fb3f116b17413bc5d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-enable-and-disable-host-initiated-sso"></a>如何啟用和停用主控件初始化的 SSO
依照預設，主控件初始化的單一登入不會在單一登入系統中啟用，且必須由 SSO 系統管理員啟用。  
  
### <a name="to-enable-host-initiated-sso-using-the-mmc-snap-in"></a>使用 MMC 嵌入式管理單元啟用主控件初始化的 SSO  
  
1.  上**啟動**功能表上，按一下 **程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  使用滑鼠右鍵按一下 **[系統]**，然後按一下 **[屬性]**。  
  
4.  按一下**選項** 索引標籤。  
  
5.  選取**啟用主控件初始化的 SSO**方塊，然後按一下**確定**。  
  
### <a name="to-enable-host-initiated-sso-using-the-command-line"></a>使用命令列啟用主控件初始化的 SSO  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssomanage-啟用 hisso**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
 停用 SSO 會套用至整個 SSO 系統，所有與主控件初始化的 SSO 相關的作業都會關閉。  
  
#### <a name="to-disable-host-initiated-sso-using-the-mmc-snap-in"></a>使用 MMC 嵌入式管理單元停用主控件初始化的 SSO  
  
1.  上**啟動**功能表上，按一下 **程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  使用滑鼠右鍵按一下 **[系統]**，然後按一下 **[屬性]**。  
  
4.  按一下**選項** 索引標籤。  
  
5.  清除**啟用主控件初始化的 SSO**方塊，然後按一下**確定**。  
  
#### <a name="to-disable-host-initiated-sso-using-the-command-line"></a>使用命令列停用主控件初始化的 SSO  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssomanage-停用 hisso**依適當情況。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>請參閱  
 [主控件初始化的 SSO](../core/host-initiated-sso.md)
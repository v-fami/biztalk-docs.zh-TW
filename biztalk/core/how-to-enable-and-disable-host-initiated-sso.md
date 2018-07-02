---
title: 如何啟用和停用主控件初始化的 SSO |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- host initiated SSO, disabling
- disabling, host initiated SSO
- enabling, host initiated SSO
- host initiated SSO, enabling
ms.assetid: a11d314a-6ff9-4d0a-89c3-c412541c2cec
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f187572f671328c77576749b1bf8f3564f025005
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979319"
---
# <a name="how-to-enable-and-disable-host-initiated-sso"></a>如何啟用和停用主控件初始化的 SSO
依照預設，主控件初始化的單一登入不會在單一登入系統中啟用，且必須由 SSO 系統管理員啟用。  
  
### <a name="to-enable-host-initiated-sso-using-the-mmc-snap-in"></a>使用 MMC 嵌入式管理單元啟用主控件初始化的 SSO  
  
1.  上**開始**功能表上，按一下**程式**，按一下  **Microsoft 企業單一登入**，然後按一下**SSO 管理**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  使用滑鼠右鍵按一下 **[系統]**，然後按一下 **[屬性]**。  
  
4.  按一下 [**選項**] 索引標籤。  
  
5.  選取 **啟用主控件初始化的 SSO**方塊，然後按一下**確定**。  
  
### <a name="to-enable-host-initiated-sso-using-the-command-line"></a>使用命令列啟用主控件初始化的 SSO  
  
1. 在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2. 在 [**執行**] 對話方塊中，輸入**cmd**，然後按一下 **[確定]**。  
  
3. 在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4. 型別**ssomanage-啟用 hisso**。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
   停用 SSO 會套用至整個 SSO 系統，所有與主控件初始化的 SSO 相關的作業都會關閉。  
  
#### <a name="to-disable-host-initiated-sso-using-the-mmc-snap-in"></a>使用 MMC 嵌入式管理單元停用主控件初始化的 SSO  
  
1.  上**開始**功能表上，按一下**程式**，按一下  **Microsoft 企業單一登入**，然後按一下**SSO 管理**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  使用滑鼠右鍵按一下 **[系統]**，然後按一下 **[屬性]**。  
  
4.  按一下 [**選項**] 索引標籤。  
  
5.  清除**啟用主控件初始化的 SSO**方塊，然後按一下**確定**。  
  
#### <a name="to-disable-host-initiated-sso-using-the-command-line"></a>使用命令列停用主控件初始化的 SSO  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在 [**執行**] 對話方塊中，輸入**cmd**，然後按一下 **[確定]**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssomanage-停用 hisso**視情況。  
  
    > [!NOTE]
    >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
## <a name="see-also"></a>另請參閱  
 [主控件初始化的 SSO](../core/host-initiated-sso.md)
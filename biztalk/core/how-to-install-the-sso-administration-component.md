---
title: 安裝 SSO 管理元件 |Microsoft 文件
description: 若要取得 SSO 管理自訂安裝和使用 ssomanage 或 SSO 管理 BizTalk Server 中輸入伺服器名稱
ms.custom: ''
ms.date: 09/27/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 096839e2-7129-498d-92ee-5afeea8dbe0d
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab2bb01defe700408a551a144eae67d0405565f4
ms.sourcegitcommit: 5355a25d120d094778fb8f68ea14cab55c68d292
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2017
ms.locfileid: "22317983"
---
# <a name="how-to-install-the-sso-administration-component"></a>如何安裝 SSO 管理元件

## <a name="overview"></a>概觀
您可以安裝企業單一登入的管理元件當做獨立功能。 若您需要以遠端方式管理 SSO 系統，這將非常有用。 軟硬體需求與一般「企業 SSO 執行階段服務」安裝一樣。  
  
 安裝管理元件之後, 您可以輸入要用於管理 SSO 伺服器。 您可以使用命令列工具 (ssomanage.exe)，或 SSO 管理 MMC 嵌入式管理單元。 本主題會列出兩個程序。  
  
 安裝 SSO 系統管理公用程式 (ssomanage.exe) 並不會在 [開始] 功能表上建立捷徑來存取命令列公用程式。 若要在安裝後執行 SSO 系統管理公用程式，您必須開啟命令提示字元中，並巡覽至 SSO 目錄在`Program Files\Common Files\Enterprise Single Sign-On`。  
  
 「企業 SSO 管理」功能也包含 MMC 嵌入式管理單元。 嵌入式管理單元至函式，必須在電腦上安裝 MMC 3.0。  
  
 若要開啟 企業 SSO MMC 嵌入式管理單元從**啟動**功能表上，選取**所有程式**，選取**Microsoft 企業單一登入**，然後**SSO管理**。  
  
## <a name="install-the-enterprise-single-sign-on-administrative-component"></a>安裝企業單一登入系統管理元件  
  
-   自訂安裝的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，並選取 企業單一登入的管理功能。 如[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，這列在**其他軟體**。  
  
## <a name="enter-the-server-using-the-mmc-snap-in"></a>輸入使用 MMC 嵌入式管理單元的伺服器  
  
1.  在目前未安裝管理元件的電腦上完成安裝後，開啟 SSO 管理嵌入式管理單元。  
  
     在**啟動**功能表上，選取**所有程式**，選取**Microsoft 企業單一登入**，然後選取**SSO 管理**。  
  
2.  在 MMC 嵌入式管理單元在**主控台根目錄**，以滑鼠右鍵按一下**企業單一登入**，然後按一下**選取**。  
  
     **選取 SSO 伺服器**對話方塊隨即出現。  
  
3.  輸入或瀏覽至您要指定的 SSO 伺服器名稱。 若要指定所有使用者的 SSO 伺服器的電腦上，選取**設定所有使用者的 SSO 伺服器**。  
  
4.  按一下 **[確定]**。  
  
## <a name="enter-the-server-using-the-command-line-tool"></a>輸入伺服器使用命令列工具  
  
1.  依序按一下 **[開始]** 及 **[執行]**，然後輸入 **cmd**。  
  
2.  在命令列提示字元中，移至「企業單一登入」安裝目錄。 預設安裝目錄是`\Program Files\Common Files\Enterprise Single Sign-On`。  
  
3.  選取下列選項的其中一個輸入 SSO 伺服器：  
  
    1.  型別**ssomanage – server**輸入您想要執行管理作業時，連接到 SSO 伺服器。  
  
         \- 或 -  
  
    2.  型別**ssomanage-serverall**輸入此電腦的所有使用者執行管理作業時將會都連接到 SSO 伺服器。  
  
## <a name="see-also"></a>另請參閱  
 [如何安裝 SSO 用戶端公用程式](../core/how-to-install-the-sso-client-utility.md)   
 [設定 SSO](../core/configuring-sso.md)   
 [安裝 SSO](../core/installing-sso.md)

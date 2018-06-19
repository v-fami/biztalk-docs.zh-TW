---
title: 如何安裝 SSO 用戶端公用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing, SSO
- SSO, client utility
- client utility [SSO]
- SSO, installing
ms.assetid: e14d257e-2fde-46af-b90c-5dbc0884536b
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4eba4e0747c9566c5303e04602d957173cc56052
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254246"
---
# <a name="how-to-install-the-sso-client-utility"></a>如何安裝 SSO 用戶端公用程式
獨立的 SSO 用戶端公用程式 (命令列公用程式，以使用者介面為基礎) 讓一般使用者可以在 SSO 資料庫中設定其用戶端對應。 SSO 用戶端公用程式是以自我解壓縮檔 (SSOClientInstall.exe) 的方式安裝，並且會隨 SSO 管理功能一併安裝。 系統管理員也可將安裝程式封裝放在網路共用上，讓用戶端使用者使用安裝程式封裝。  
  
 若要安裝 SSO 用戶端公用程式，用戶端電腦必須執行下列其中一種作業系統：  
  
-   [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
-   [!INCLUDE[btsDotNetFramework3.5](../includes/btsdotnetframework3-5-md.md)]或[!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)](只需要如果您使用 UI 型 SSO 用戶端公用程式，或是要應用企業單一登入的 managed 互通性元件)。  
  
 安裝 SSO 用戶端公用程式之後, 您可以啟動此**啟動**功能表按一下**程式**， **Microsoft 企業單一登入**，然後**SSO 用戶端公用程式**。  
  
### <a name="to-install-the-sso-client-utility"></a>安裝 SSO 用戶端公用程式  
  
1.  按兩下安裝程式封裝 SSOClientInstall。  
  
    > [!NOTE]
    >  向您的「企業單一登入系統管理員」詢問此檔案在您企業中的位置。  
  
     **WinZip 自我解壓縮程式**程式隨即出現。  
  
2.  選取您要解壓縮檔案，然後按一下的資料夾**解壓縮**。  
  
     建議將檔案解壓縮至暫存資料夾。  
  
     **企業單一登入用戶端安裝**程式隨即出現。  
  
3.  在**歡迎使用 「 企業單一登入用戶端**頁面上，按一下**下一步**。  
  
4.  在 授權合約 頁面中，按一下 **我接受授權合約中的條款**，然後按一下 **下一步**。  
  
5.  在**使用者資訊**頁面上，輸入您的使用者名稱、 組織名稱，然後按一下**下一步**。  
  
6.  在**開始安裝**頁面上，按一下**安裝**。  
  
7.  在**完成企業單一登入用戶端精靈**頁面上，按一下**完成**。  
  
8.  執行下列其中一項動作以指定 SSO 伺服器：  
  
    -   開啟 ENTSSO 管理 MMC 嵌入式管理單元。 **選取 SSO 伺服器**對話方塊隨即出現。 輸入或瀏覽到您在執行管理作業時希望連接的 SSO 伺服器。 若要指定所有使用者的 SSO 伺服器電腦上，選取**設定所有使用者的 SSO 伺服器**。  
  
         OR  
  
    -   在命令提示字元中，輸入`ssomanage –server`來指定所需的 SSO 伺服器。 您也可以輸入`ssomanage -serverall`以指定執行管理作業時，此電腦的所有使用者將都連線到 SSO 伺服器。  
  
## <a name="see-also"></a>另請參閱  
 [如何安裝 SSO 管理元件](../core/how-to-install-the-sso-administration-component.md)   
 [設定 SSO](../core/configuring-sso.md)   
 [安裝 SSO](../core/installing-sso.md)
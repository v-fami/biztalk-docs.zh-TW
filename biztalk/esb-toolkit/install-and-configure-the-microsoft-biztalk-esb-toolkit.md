---
title: 安裝和設定 Microsoft BizTalk ESB Toolkit |Microsoft 文件
description: 安裝和設定 BizTalk Server 上的 ESB Toolkit 的步驟-步驟指示
caps.latest.revision: 8
author: MandiOhlinger
manager: anneta
ms.custom: ''
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 698843f7-8361-4d02-9278-0e66f2a9f472
ms.author: mandia
ms.openlocfilehash: 33805fe58298e4f4729161a62742d3b204996b00
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22296998"
---
# <a name="install-and-configure-the-microsoft-biztalk-esb-toolkit"></a>安裝和設定 Microsoft BizTalk ESB Toolkit
從 BizTalk Server 2013 和較新版本，[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]與整合[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝程式。 本主題說明如何安裝及設定[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，而且也包含社群寫入升級 ESB Toolkit 連結。  
  
> [!IMPORTANT]
>  您必須先安裝 BizTalk Server，才能開始安裝 [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]。  
  
## <a name="install"></a>安裝 
  
1.  執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]以系統管理員身分的 setup.exe 檔案。 在 [安裝] 選取**安裝[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]** 。  
  
2.  接受授權合約，然後再選取**下一步**。  
  
3.  在 [元件安裝] 中，選取您想要安裝的元件，然後選取 [下一步]。  
  
4.  在**摘要**，檢閱 功能選擇，，然後選取**安裝**。  
  
5.  選取 [完成] 以關閉安裝精靈。  

An install log file is created, similar to `C:\Users\yourUserName\AppData\Local\Temp\Setup(081017 175042).htm'. 
  
## <a name="configure"></a>設定 
  
> [!IMPORTANT]
>  您必須先設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之後，才能設定 [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]。  
  
1.  從**啟動**功能表上，選取**Microsoft [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]** ，然後選取**ESB 組態工具**。  
  
    > [!IMPORTANT]
    >  系統管理員身分執行 ESB 組態工具。  
  
2.  在組態中，選取**資料庫伺服器**。 輸入主控資料庫伺服器名稱[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]資料庫。   
  
3.  在**IIS Web 服務**，輸入使用者帳戶和執行的 IIS 應用程式所建立的密碼[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]。 接下來，輸入裝載應用程式的 IIS 網站。  
  
4.  **BizTalk 使用者群組**列出預設的使用者群組通常用於 ESB 組態。  
  
    > [!IMPORTANT]
    >  在這個階段，您可以選取**套用組態**設定[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]使用這些預設設定。 不過，如果您想要自訂的組態，完成其餘步驟。 以您在下一個步驟中輸入的值優先於預設值。  
  
5.  在左窗格中，依序展開**ESB 組態**，依序展開 * * 例外狀況管理 * *，然後：  
  
    -   如果您不想設定例外狀況的管理資料庫，然後選取**資料庫**，並取消核取**啟用例外狀況管理資料庫**。
  
    -   如果您想要使用現有的資料庫，而不是建立新的資料庫，然後選取 **資料庫**，然後選取**使用現有的資料庫**。 輸入資料庫伺服器名稱和資料庫名稱。  
  
    -   如果您不想設定例外狀況的 web 服務，然後選取**例外狀況的 Web 服務**，並取消核取**啟用例外狀況 Services**。  如果您想要執行這些服務在不同的網站，您可以在此處輸入。  
  
6.  在左窗格中，依序展開**ESB 核心元件**，然後：  
  
    -   如果您不想設定路線的資料庫，然後選取**路線資料庫**，並取消核取**路線資料庫**。  
  
    -   如果您想要使用現有的路線資料庫，然後選取**路線資料庫**，然後選取**使用現有的資料庫**。 輸入資料庫伺服器名稱和資料庫名稱。  
  
    -   如果您不想要設定這些 web 服務，然後選取**核心 Web 服務**，並取消核取**啟用核心服務**。 如果您想要執行這些服務在不同的網站，您可以在此處輸入。
  
7.  在左窗格中，選取**組態**。  
    如果您安裝與設定[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]在單一伺服器環境中，選取**檔案組態來源**。 如果您要設定多電腦部署，請選取**SSO 組態來源**，然後輸入下列：  
  
    -   **SSO 伺服器**： 輸入 SSO 伺服器名稱
  
    -   **組態檔**： 選取省略符號 **（...）**，然後瀏覽至 esb.config 檔案 (\Program Files (x86) \Microsoft BizTalk ESB Toolkit)
  
    -   **應用程式名稱**： 輸入 SSO 應用程式的名稱。 例如，輸入`ESB Toolkit`。  
  
    -   **連絡資訊**： 以下列格式輸入有效的電子郵件地址的適當的連絡資訊： `someone@example.com`。  
  
    -   **系統管理員群組名稱**： 選取省略符號 **（...）**，然後瀏覽至適當的系統管理員群組  
  
    -   **使用者群組名稱**： 選取省略符號 **（...）**，然後瀏覽至適當的群組  

8.  選取**套用組態**。 開啟 IIS，您會發現在設定 [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] 時指定的網站下方，現已建立 [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] 所需的應用程式。  
  
9. 在**ESB 組態工具**，選取**ESB BizTalk 應用程式**，然後：  
  
    -   選取**BizTalk Server 中啟用 ESB 核心元件**建立應用程式中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 選取**使用預設繫結**預設主控件到這個應用程式繫結。 選取**不使用預設繫結**如果您不想要繫結至預設主控件應用程式。 在此案例中，您必須明確繫結至主機應用程式建立應用程式之後。  
  
    -   選取**BizTalk Server 中啟用 ESB JMS/WMQ 元件**建立應用程式中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 選取**使用預設繫結**預設主控件到這個應用程式繫結。 選取**不使用預設繫結**如果您不想要繫結至預設主控件應用程式。 在此案例中，您必須明確繫結至主機應用程式建立應用程式之後。  
  
    -   選取**套用組態**建立您所選取的應用程式。 確認應用程式已在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中建立。  
  
## <a name="upgrade-esb-toolkit--community-addition"></a>升級 ESB Toolkit – 社群補充  
 [就地升級至 2.2 ESB Toolkit 2.1](http://www.brianloesgen.com/blog/2013/10/10/in-place-upgrade-of-esb-toolkit-21-to-22.html) (http://www.brianloesgen.com/blog/2013/10/10/in-place-upgrade-of-esb-toolkit-21-to-22.html)

## <a name="see-also"></a>另請參閱
[疑難排解安裝問題，以及一般錯誤和解析度](troubleshooting-the-biztalk-esb-toolkit.md)
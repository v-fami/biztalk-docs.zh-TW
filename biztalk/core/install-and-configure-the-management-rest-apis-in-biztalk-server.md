---
title: "安裝和設定管理 REST Api |Microsoft 文件"
description: "查詢中使用管理資料 REST Api 與 BizTalk Server 中的功能組件 1 BizTalk 環境的成品的狀態"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 39442756-5886-4ddd-b700-3800a237de4a
caps.latest.revision: "8"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 009b3b0bb333b8f92f6235da57b0c3e9f5daca96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="install-and-configure-the-management-rest-apis-in-biztalk-server"></a>安裝和設定 BizTalk Server 中的管理 REST Api
若要啟用遠端管理的 REST Api 中使用 Windows PowerShell 指令程式[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。

## <a name="what-are-management-data-apis"></a>管理資料應用程式開發介面有哪些？
管理資料應用程式開發介面是可讓您從遠端更新、 加入及查詢中的不同成品的狀態的端點您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境。 端點會新增使用 REST，並隨附 Swagger 定義。 

**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，沒有安裝這些 REST Api，以及其 swagger 定義的 Windows PowerShell 指令碼。 這些 Api 進行遠端管理連接埠、 協調流程、 夥伴、 協議、 管線和更多的 REST 呼叫。 

本主題說明如何安裝 REST Api。

## <a name="prerequisites"></a>必要條件
* 安裝[功能套件 1](https://www.microsoft.com/download/details.aspx?id=55100)上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]

* 在上安裝 IIS [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。 在大部分[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境中，IIS 已安裝。 請參閱[硬體和軟體需求適用於 BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)。

## <a name="enable-the-rest-apis"></a>啟用 REST Api

1. 以系統管理員身分執行 Windows PowerShell (**啟動**功能表中，輸入**PowerShell**，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**)。 
2. 瀏覽至 [BizTalk] 資料夾下**Program Files (x86)/Microsoft BizTalk Server 2016**
3. 執行下列命令。 請務必更新您`website`， `domain/user`， `password`，和`domain\group`以您的值： 

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service management -WebSiteName '<Default Web Site>' -ApplicationPool <mgmtServiceAppPool> -ApplicationPoolUser <domain>\<user> -ApplicationPoolUserPassword <password> -AuthorizationRoles '<domain>\<group>, <domain>\<group>'
    ```
4. 執行指令碼之後，瀏覽新的 IIS 應用程式：  
    1. 開啟網頁瀏覽器
    2. 瀏覽至**http://localhost/OperationalDataService/swagger**

5. Swagger 定義負載。 您也可以變更誰可以存取藉由更新**web.config**管理應用程式的根資料夾中的檔案。

REST Api 公開會透過此機器，以及可以存取和其他應用程式執行。 


## <a name="see-also"></a>另請參閱
 [設定此功能套件](../core/configure-the-feature-pack.md)
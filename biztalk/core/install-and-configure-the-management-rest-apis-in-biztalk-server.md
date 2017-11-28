---
title: "安裝和設定管理 REST Api |Microsoft 文件"
description: "查詢您使用管理資料 REST Api 與 BizTalk Server 中的功能組件的 BizTalk 環境中的成品"
ms.custom: fp1
ms.date: 11/06/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 39442756-5886-4ddd-b700-3800a237de4a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c207b0aca5f2673e615167f75f7f1c7c3fb0e042
ms.sourcegitcommit: f65e8ed2b8c18cded26b9d60868fb6a56bcc1205
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="install-and-configure-the-management-rest-apis-in-biztalk-server"></a>安裝和設定 BizTalk Server 中的管理 REST Api

## <a name="what-are-management-data-apis"></a>管理資料應用程式開發介面有哪些？
管理資料應用程式開發介面是端點可讓您從遠端更新、 加入及查詢中的不同成品的狀態，您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境。 端點會新增使用 REST，並隨附 swagger 定義。 

**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，沒有安裝這些 REST Api，以及其 swagger 定義的 Windows PowerShell 指令碼。 這些 Api 進行遠端管理連接埠、 協調流程、 夥伴、 協議、 管線和更多的 REST 呼叫。 

## <a name="prerequisites"></a>必要條件
* 安裝[功能套件 2](https://aka.ms/bts2016fp2)上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]

* 在上安裝 IIS [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。 在大部分[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境中，IIS 已安裝。 請參閱[硬體和軟體需求適用於 BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)。 確認 IIS 已安裝 BizTalk Server 上開啟**Internet Information Services 管理員**。 

## <a name="step-1-install-the-rest-apis"></a>步驟 1： 安裝 REST Api

1. 以系統管理員身分執行 Windows PowerShell (**啟動**功能表中，輸入**PowerShell**，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**)。 
2. 移至 BizTalk 安裝資料夾 (例如，輸入： `cd 'C:\Program Files (x86)\Microsoft BizTalk Server 2016\'`)。
3. 在下列文字，取代`Default Web Site`， `mgmtServiceAppPool`， `domain/user`， `password`，和`domain\group`以您的值：

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service management -WebSiteName '<Default Web Site>' -ApplicationPool <mgmtServiceAppPool> -ApplicationPoolUser <domain>\<user> -ApplicationPoolUserPassword <password> -AuthorizationRoles '<domain>\<group>, <domain>\<group>'
    ```

    在下列範例中，我們使用`Default Web Site`，建立名為應用程式集區`RESTAppPool`，執行做為 appPool`bootcampbts2016\btsservice`帳戶，請使用`BIZTALK-serviceacct`做為使用者帳戶密碼，並提供 BizTalk Server 系統管理員群組的權限。 請務必輸入下列項目，包括單一引號周圍有空格的值： 

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service management -WebSiteName 'Default Web Site' -ApplicationPool RESTAppPool -ApplicationPoolUser bootcampbts2016\btsservice -ApplicationPoolUserPassword  BIZTALK-serviceacct -AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'
    ```

    完成時， **BizTalkManagementService**在 IIS 中建立應用程式：  
    ![BizTalkManagementService 應用程式](../core/media/biztalkmanagementservice-apppool.png)

4. 若要確認它是否運作，瀏覽至`http://localhost/BizTalkManagementService/swagger`。 如果系統會提示您登入，是您在上一個步驟中輸入 「 網域 \ 群組成員的帳戶登入 (`-AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'`)。 

> [!WARNING]
> 在 IIS 中的 BizTalkManagementService 應用程式會使用 web.config 檔案。 在 web.config 中的項目**會區分大小寫**。 因此當您執行 Windows PowerShell 指令碼時，必須輸入正確的大小寫的`-AuthorizationRoles`值。 如果您不確定的情況下，以下是可以輕鬆地找出： 
> 
> 1. 開啟**電腦管理**，然後展開**本機使用者和群組**。
> 2. 選取**群組**，向下捲動至**SQLServer...** 群組。 
> 3. 在下列範例中，請注意**BOOTCAMPBTS2016**中全部大寫。 如果您看到全部大寫，然後在 全部大寫中輸入電腦名稱。 
> 
> ![電腦名稱是以全部大寫](../core/media/groups-case.png)

現在，透過 IIS 公開 REST Api，它們可以存取及執行其他應用程式。 

您可以變更誰可以存取透過手動更新**web.config**檔案也會管理應用程式的根資料夾中。 例如，使用下列命令以允許任何人存取 swagger 輸出： 

```
<authorization>
   <allow users="*" />
</authorization>
```

## <a name="step-2-test-the-apis"></a>步驟 2： 測試應用程式開發介面

1. 在 BizTalk 伺服器上，瀏覽至`http://localhost/BizTalkManagementService/swagger`。

2. 捲動到**主機**，然後選取**顯示/隱藏**。 沒有 GET 命令，按一下此資料列：  
![取得所有主機](../core/media/managment-rest-apis-hosts-get.png)

3. 它會顯示詳細資料。 選取**現在就試試看**:  
![現在就試試看](../core/media/managment-rest-apis-hosts-tryitout.png)

4. 回應主體會傳回所有主機：  
![回應](../core/media/managment-rest-apis-hosts-response.png)

> [!NOTE]
> 如果您瀏覽至`http://localhost/BizTalkManagementService`，您應該取得 500 錯誤。 這是個好方法。 只要加入`/swagger`結尾 URL，而且您會看到可用的 REST Api。 


## <a name="see-also"></a>另請參閱
 [設定此功能套件](../core/configure-the-feature-pack.md)
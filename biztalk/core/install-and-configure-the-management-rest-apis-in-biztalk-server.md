---
title: 安裝和設定管理 REST Api |Microsoft Docs
description: 查詢中使用管理資料 REST Api 搭配 BizTalk Server 中的 Feature Pack BizTalk 環境的成品
ms.custom: fp1
ms.date: 02/25/2019
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39442756-5886-4ddd-b700-3800a237de4a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 680b7390462a7a64d3064f621b2011952ba2551c
ms.sourcegitcommit: 0e14c3e018b091d81d0e4a68fafc10f6e31697e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56828563"
---
# <a name="install-and-configure-the-management-rest-apis-in-biztalk-server"></a>安裝和設定 BizTalk Server 中的管理 REST Api

## <a name="what-are-management-data-apis"></a>管理資料的 Api 有哪些？
管理資料的 Api 是可讓您從遠端更新、 加入及查詢中的不同成品的狀態端點您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境。 將端點新增使用其餘部分，並隨附的 swagger 定義。 

**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，沒有安裝這些 REST Api 和其 swagger 定義的 Windows PowerShell 指令碼。 這些 Api 進行 REST 呼叫，從遠端管理連接埠、 協調流程、 合作夥伴、 合約、 管線和更多功能。 

若要查看可用的 Api，以及您可以做什麼，請參閱[功能套件的 REST API 參考](https://docs.microsoft.com/rest/api/biztalk/?view=rest-biztalk-2016)。

## <a name="prerequisites"></a>先決條件
* 安裝[Feature Pack 2](https://aka.ms/bts2016fp2)上您 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]

* 在上安裝 IIS [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。 確認 IIS 已安裝 BizTalk Server 上開啟**Internet Information Services 管理員**。 

  在大部分[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境中，IIS 已安裝。 請參閱[硬體和軟體需求適用於 BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)。 

## <a name="step-1-install-the-rest-apis"></a>步驟 1：安裝 REST Api

1. 以系統管理員身分執行 Windows PowerShell (**開始**功能表 > 型別**PowerShell** > 以滑鼠右鍵按一下 >**系統管理員身分執行**)。 
2. 移至 BizTalk 安裝資料夾 (例如，輸入： `cd 'C:\Program Files (x86)\Microsoft BizTalk Server 2016\'`)。
3. 在下列文字，取代`Default Web Site`， `mgmtServiceAppPool`， `domain/user`， `password`，和`domain\group`以您的值：

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service management -WebSiteName '<Default Web Site>' -ApplicationPool <mgmtServiceAppPool> -ApplicationPoolUser <domain>\<user> -ApplicationPoolUserPassword <password> -AuthorizationRoles '<domain>\<group>, <domain>\<group>'
    ```

    在下列範例中，我們會使用`Default Web Site`，建立名為應用程式集區`RESTAppPool`，執行為 appPool`bootcampbts2016\btsservice`帳戶，請使用`BIZTALK-serviceacct`做為使用者帳戶密碼，並提供 BizTalk Server 系統管理員群組權限。 請務必輸入下列項目，包括單一引號周圍有空格的值： 

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service management -WebSiteName 'Default Web Site' -ApplicationPool RESTAppPool -ApplicationPoolUser bootcampbts2016\btsservice -ApplicationPoolUserPassword  BIZTALK-serviceacct -AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'
    ```

    完成時， **BizTalkManagementService**在 IIS 中建立應用程式：  
    ![BizTalkManagementService 應用程式](../core/media/biztalkmanagementservice-apppool.png)

4. 若要確認它是否能運作，瀏覽至`http://localhost/BizTalkManagementService/swagger`。 如果系統會提示您登入、 使用您在上一個步驟中輸入 「 網域 \ 群組的成員帳戶登入 (`-AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'`)。 

> [!WARNING]
> 在 IIS 中 BizTalkManagementService 應用程式在 web.config 檔案中。 在 web.config 中的項目**區分大小寫**。 因此當您執行 Windows PowerShell 指令碼，請務必輸入正確的大小寫的`-AuthorizationRoles`值。 如果您不確定的情況下，以下是簡單的方法，若要了解： 
> 
> 1. 開啟**電腦管理**，展開**本機使用者和群組**。
> 2. 選取 **群組**，向下捲動至**SQLServer...** 群組。 
> 3. 在下列範例中，請注意**BOOTCAMPBTS2016**是全部大寫字。 如果您看到全部大寫，然後輸入電腦名稱全部大寫。 
> 
> ![電腦名稱是全部大寫字](../core/media/groups-case.png)

現在，透過 IIS 公開 REST Api，它們可以存取及執行其他應用程式。 [功能套件的 REST API 參考](https://docs.microsoft.com/rest/api/biztalk/?view=rest-biztalk-2016)列出的 Api。

您可以變更誰可以存取透過手動更新**web.config**檔案，這是管理應用程式的根資料夾中。 例如，使用下列命令來允許任何人存取 swagger 輸出： 

```
<authorization>
   <allow users="*" />
</authorization>
```

## <a name="step-2-test-the-apis"></a>步驟 2：測試 Api

1. 在 BizTalk 伺服器上，瀏覽至`http://localhost/BizTalkManagementService/swagger`。

2. 捲動到 **主機**，然後選取**顯示/隱藏**。 沒有 GET 命令;按一下此資料列：  
![取得所有主機](../core/media/managment-rest-apis-hosts-get.png)

3. 它會顯示詳細資料。 選取 **試用看看**:  
![現在就試試看](../core/media/managment-rest-apis-hosts-tryitout.png)

4. 回應主體會傳回所有主機：  
![回應](../core/media/managment-rest-apis-hosts-response.png)

> [!NOTE]
> 如果您瀏覽至`http://localhost/BizTalkManagementService`，您應該取得 500 錯誤。 這是一件好事。 只要加入`/swagger`結尾的 URL，而且您會看到可用的 REST Api。 


## <a name="see-also"></a>另請參閱
 [設定 Feature Pack](../core/configure-the-feature-pack.md)
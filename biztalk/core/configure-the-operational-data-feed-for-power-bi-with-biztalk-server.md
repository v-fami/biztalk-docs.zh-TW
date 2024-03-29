---
title: 讓 Power BI |Microsoft Docs
description: 安裝 BizTalk Server 功能套件在 Power BI 範本
ms.custom: fp1
ms.date: 6/26/2018
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe6d3a97-c7c0-4147-baa9-ee12f93248eb
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bfe842e3b131e6b0fcde75485c1d472320644c3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994175"
---
# <a name="configure-the-power-bi-operational-data-feed-in-biztalk-server"></a>設定 Power BI 操作資料，使用 BizTalk Server 中的摘要

**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** 、 將追蹤傳送至 Power BI 使用的 Power BI 範本，或建立您自己。 

## <a name="what-is-operational-data"></a>什麼是作業中的資料
操作資料是有關的執行個體和郵件流經您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境。 操作資料摘要是相同的資料取得查看中的 群組中樞[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]。 資料存取，並使用視覺效果工具，包括 Power BI 查詢。 

摘要包含下列資料表：
* 應用程式資料
* AS2 狀態記錄
* 批次資訊
* 執行個體資訊
* 交換彙總記錄
* 交換狀態記錄
* 訊息
* 訂閱
* 追蹤的事件
* 交易報表
* 交易集

> [!TIP]
> [PowerBI.com](http://powerbi.microsoft.com)是了解並深入了解 Power BI 的絕佳資源。

## <a name="prerequisites"></a>必要條件
* 下載並安裝[Power BI Desktop](https://powerbi.microsoft.com/desktop/)擁有網路存取權的任何電腦上您 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]
* 安裝[Feature Pack 2](https://aka.ms/bts2016fp2)，或更新版本上的功能組件中，您 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]
* 在上安裝 IIS [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。 在大部分[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境中，IIS 已安裝。 請參閱[硬體和軟體需求適用於 BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)。 確認 IIS 已安裝 %installationdirectory **Internet Information Services 管理員**。 
* 選擇性。 安裝和設定[Power BI Gateway](https://powerbi.microsoft.com/gateway/)連接[PowerBI.com](http://powerbi.microsoft.com)與您內部部署的 BizTalk Server。 如果您不使用內部部署 BizTalk Server，您不需要閘道。

## <a name="step-1-enable-operational-data"></a>步驟 1： 啟用操作資料

1. 以系統管理員身分執行 Windows PowerShell (**開始**功能表中，輸入**PowerShell**，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**)。 
2. 移至 BizTalk 安裝資料夾 (例如，輸入： `cd 'C:\Program Files (x86)\Microsoft BizTalk Server 2016\'`)。
3. 在下列文字，取代`Default Web Site`， `operationalDataServiceAppPool`， `domain\user`， `password`，和`domain\group`以您的值：

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service operationaldata -WebSiteName '<Default Web Site>' -ApplicationPool <operationalDataServiceAppPool> -ApplicationPoolUser <domain>\<user\> -ApplicationPoolUserPassword <password> -AuthorizationRoles '<domain>\<group1\>, <domain>\<group2\>, <domain>\<user\>, <domain>\<user2\>'
    ```

   * **服務**： 若要設定服務 (**OperationalData**適用於 Power BI)
   * **WebSiteName**： 現有的 IIS 網站上裝載服務。 預設值是**Default Web Site**。
   * **ApplicationPool**： 服務所使用的應用程式集區。 若有的話，不會建立一個新。 預設值是**DefaultAppPool**。
   * **ApplicationPoolUser**： 設定應用程式集區，以做為此使用者的身分識別執行。 必須具有 BizTalk Server 操作員或更高的權限。
   * **ApplicationPoolUserPassword**: ApplicationPoolUser 密碼
   * **AuthorizationAccount**： 已獲授權的群組或使用者可以使用此服務的清單

     在下列範例中，我們會使用`Default Web Site`，建立名為應用程式集區`PowerBIAppPool`，執行為 appPool`bootcampbts2016\btsservice`帳戶，請使用`BIZTALK-serviceacct`做為使用者帳戶密碼，並提供`BizTalk Server Administrators`群組權限。 請務必輸入下列項目，包括單一引號周圍有空格的值： 

     ```Powershell
     FeaturePack.ConfigureServices.ps1 -Service operationaldata -WebSiteName 'Default Web Site' -ApplicationPool PowerBIAppPool -ApplicationPoolUser bootcampbts2016\btsservice -ApplicationPoolUserPassword  BIZTALK-serviceacct -AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'
     ```

     完成時，就會在 IIS 中建立 BizTalkOperationalDataService 應用程式：  
     ![BizTalkMOperationalDataServer 應用程式](../core/media/biztalkmanagementservice-apppool.png)


4. 若要確認它是否能運作，瀏覽至`http://localhost/BizTalkOperationalDataService`。 

    如果系統會提示您登入、 使用您在上一個步驟中輸入 「 網域 \ 群組的成員帳戶登入 (`-AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'`)。 

    如果系統提示您開啟或儲存 BizTalkOperationalDataService.json，然後完成您的安裝。 您可以將它儲存在本機，然後再將它開啟在記事本或 Visual Studio 以查看內容中。 

> [!WARNING]
> 在 IIS 中 BizTalkOperationalDataService 應用程式在 web.config 檔案中。 在 web.config 中的項目**區分大小寫**。 因此當您執行 Windows PowerShell 指令碼，請務必輸入正確的大小寫的`-AuthorizationRoles`值。 如果您不確定的情況下，以下是簡單的方法，若要了解： 
> 
> 1. 開啟**電腦管理**，展開**本機使用者和群組**。
> 2. 選取 **群組**，向下捲動至**SQLServer...** 群組。 
> 3. 在下列範例中，請注意**BOOTCAMPBTS2016**是全部大寫字。 如果您看到全部大寫，然後輸入電腦名稱全部大寫。 
> 
> ![電腦名稱是全部大寫字](../core/media/groups-case.png)

## <a name="step-2-use-the-template-in-power-bi"></a>步驟 2： 在 Power BI 中使用範本

1. 下載並安裝[Power BI Desktop](https://powerbi.microsoft.com/desktop/) BizTalk 伺服器上。 您可以選取以開啟它，這是選擇性。 如果您有工作或學校帳戶，您可能會有存取 Power BI。 請嘗試登入該帳戶。 或者，您可以免費試用註冊之後。 
2. 開啟`\Program Files (x86)\Microsoft BizTalk Server 2016\OperationalDataService`資料夾，然後開啟`BizTalkOperationalData.pbit`檔案：  
![開啟 pbit 檔案](../core/media/operational-data-pbit.png)

3. Power BI desktop 便會開啟，並會提示您輸入的 URL。 輸入`http://localhost/<yourWebSite>`您建立的 OData 摘要的 URL。 例如，輸入`http://localhost/BizTalkOperationalDataService`。 您的 URL 看起來如下所示：  
![輸入的 URL](../core/media/operational-data-url.png)

4. 選取 **負載**。 載入視窗，並連接到不同的 oData 來源 BizTalkOperationalDataService.json 檔案中。 完成之後，儀表板會顯示您環境的詳細資料。

## <a name="couldnt-authenticate"></a>無法驗證
如果您收到`couldn't authenticate with the credentials provided`訊息類似於下列項目，則很可能您的應用程式集區身分識別沒有足夠的存取權，BizTalk Server 資料庫。 您可以變更 IIS 中的應用程式集區識別至具有更多的權限的帳戶可能是您的登入的使用者帳戶 （其具有本機系統管理員權限）。 

![無法使用提供的認證進行驗證](../core/media/operational-data-authentication-error.png)

## <a name="do-more"></a>執行更多作業
這只是開端。 Power BI 也會有可以在內部部署 BizTalk Server 安裝閘道。 使用閘道時，可以發佈您的儀表板，取得即時資料，並建立排程來重新整理儀表板。 下列部落格直接挑明解詳述這些步驟： 

* [如何發佈 Power BI – 逐步設定上的 BizTalk 作業資料](https://blog.sandro-pereira.com/2017/05/07/biztalk-server-2016-feature-pack-1-how-to-publish-biztalk-operational-data-power-bi-step-by-step-configuration-part-3/)

[引導式學習](https://powerbi.microsoft.com/guided-learning/)也是深入了解 Power BI 中，以及您可以執行的所有事項的最佳去處。 

## <a name="see-also"></a>另請參閱

[深入了解 Power BI](https://www.powerbi.com)  
[設定 Feature Pack](../core/configure-the-feature-pack.md)

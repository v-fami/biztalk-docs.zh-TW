---
title: "設定操作資料摘要與 BizTalk Server 的 Power bi |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe6d3a97-c7c0-4147-baa9-ee12f93248eb
caps.latest.revision: "11"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 09b1b1fd7f350e168b2bb13d6bee2e45c12d49cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-operational-data-feed-for-power-bi-with-biztalk-server"></a>設定操作資料摘要與 BizTalk Server 的 Power bi
讀取透過 oData 摘要中所提供的操作資料[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。 

**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** 、 將追蹤傳送到 Power BI 使用 Power BI 範本提供，或建立您自己。 

## <a name="what-is-operational-data"></a>什麼是操作資料
操作資料是有關的執行個體和訊息通過您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境。 操作資料摘要是相同的資料取得查看中的 群組中樞[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]主控台。 可存取的資料，且查詢使用視覺化工具，包括 Power BI。 

摘要會包含下表的資料：
* 應用程式資料
* AS2 狀態記錄
* 批次的資訊
* 執行個體資訊
* 交換彙總記錄
* 交換狀態記錄
* 訊息
* 訂閱
* 追蹤的事件
* 交易報表
* 交易集

> [!TIP]
> [PowerBI.com](http://powerbi.microsoft.com)是了解，並深入了解 Power BI 的絕佳資源。

## <a name="prerequisites"></a>必要條件
* 下載並安裝[Power BI Desktop](https://powerbi.microsoft.com/desktop/)擁有網路存取權的任何電腦上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]
* 安裝[功能套件 1](https://www.microsoft.com/download/details.aspx?id=55100)上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]
* 在上安裝 IIS [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。 在大部分[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境中，IIS 已安裝。 請參閱[硬體和軟體需求適用於 BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)。 

## <a name="enable-operational-data-feed"></a>啟用操作的資料摘要

1. 以系統管理員身分執行 Windows PowerShell (**啟動**功能表中，輸入**PowerShell**，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**)。 
2. 瀏覽的資料夾位置[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]安裝**Program Files (x86)/Microsoft BizTalk Server 2016**
3. 執行下列命令。 請務必更新您`website`， `domain\user`， `password`，和`domain\group`以您的值： 

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service operationaldata -WebSiteName '<Default Web Site>' -ApplicationPool <operationalDataServiceAppPool> -ApplicationPoolUser <domain>\<user> -ApplicationPoolUserPassword <password> -AuthorizationRoles '<domain>\<group1>, <domain>\<group2>'
    ```
4. 執行指令碼之後，瀏覽新的 IIS 應用程式：  
    1. 開啟網頁瀏覽器
    2. 移至**http://localhost/BizTalkOperationalDataService**

## <a name="use-the-power-bi-template"></a>使用 Power BI 範本
若要存取 Power BI 範本檔案，並使用 microsoft 提供的視覺效果，使用下列步驟：

1. 下載並安裝[Power BI Desktop](https://powerbi.microsoft.com/desktop/)。
2. 瀏覽至您的 BizTalk Server 資料夾下**Program Files (x86) \Microsoft BizTalk Server 2016\OperationalDataService**。
3. 開啟**BizTalkOperationalData.pbit**檔案。
4. 當系統提示您從 Power BI，貼上**http://localhost/\<yourWebSite\>** 您建立的 OData 摘要的 URL。 例如，輸入**http://localhost/OperationalDataService**。 

    您的 URL 看起來如下所示： 
    
    ![貼上 Power BI 範本檔案的 OData URL](../core/media/pasteurltopowerbitempaltefile.PNG)

5. 選取**負載**來填入您的 Power BI 報表中的欄位。 
6. 範本檔案會自動產生的資訊和可用的資料表，從 OData 摘要。

操作資料公開透過電腦和可存取，並根據權限的其他應用程式執行。 

若要深入了解 Power BI 中，以及如何發佈報表線上移至[PowerBI.com](http://powerbi.microsoft.com)

## <a name="see-also"></a>另請參閱

[深入了解 Power BI](https://www.powerbi.com)  
[設定此功能套件](../core/configure-the-feature-pack.md)
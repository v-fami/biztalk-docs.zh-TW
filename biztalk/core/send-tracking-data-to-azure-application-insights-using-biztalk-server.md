---
title: "將追蹤資料傳送至 Azure Application Insights 使用 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3ff6cb9-44d0-46cd-9b4f-a346365afb7b
caps.latest.revision: "10"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: f587c3049e191505c87ba456b5ddfd41011862c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="send-tracking-data-to-azure-application-insights-using-biztalk-server"></a>將追蹤資料傳送至 Azure Application Insights 使用 BizTalk Server
傳送[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]Azure 應用程式 Inisights 追蹤資料。 

**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，您可以處理，並將您的追蹤資料傳送至 Azure Application Insights。 使用 Application Insights 功能來追蹤您的執行個體從接收埠、 傳送埠和協調流程。

## <a name="prerequisites"></a>必要條件
* 建立的新執行個體[Application Insights](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-create-new-resource)
* 安裝[功能套件 1](https://www.microsoft.com/download/details.aspx?id=55100)上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]

## <a name="enable-analytics-for-your-environment"></a>啟用分析為您的環境

1. 開啟**BizTalk Server 管理**主控台中，展開**BizTalk 管理**，以滑鼠右鍵按一下**BizTalk 群組**，然後選取**設定**. 
2. 請檢查**啟用群組層級分析**。
3. 如**目標類型**，選取**Application Insight**從清單中。
4. 如**連接參數**，輸入您的 Application Insights **[檢測金鑰](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-create-new-resource)** （可在 Azure 入口網站）。

    群組設定看起來如下所示： 

    ![啟用分析為您的環境](../core/media/environmentsettingapplicationinishgt.PNG)

5. 選取 [確定] 儲存您的變更。 

一旦啟用[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]已準備好傳送至 Application Insights 資料。 接下來，啟用您的連接埠和協調流程上的分析。 

## <a name="enable-analytics-on-your-artifacts"></a>啟用您的成品上的分析

1. 在 BizTalk Server 管理，以滑鼠右鍵按一下**接收埠**，**傳送埠**或**協調流程**，然後選取**追蹤**。
2. 在下**分析**，檢查**啟用分析**。 這項設定會啟動追蹤，以及將傳送至 Application Insights 從成品資料。

    成品設定看起來如下所示： 
    
    ![協調流程的追蹤資料](../core/media/orchestrationsettingsapplicationinsight.PNG)

3. 選取 [確定] 儲存您的變更。

接下來，執行以查看您的資料的 Application Insights 中的查詢。  

> [!TIP]
> 若要深入組織資料的更多其他系統連接 BizTalk Server 的分析。

## <a name="run-queries-on-your-data"></a>在您的資料上執行查詢
一旦將資料傳送至 Application Insights，您可以使用在 Azure 中的分析工具來建立進階的查詢、 及分析您的資料。

1. 登入[Azure 入口網站](https://portal.azure.com)。
2. 開啟 Application Insights 資源，並選取**分析**。
3. 選取**使用量**，並執行所提供的查詢。

    > [!TIP]
    > 深入了解如何在 Application Insights 中撰寫查詢[Application Insights 中的分析](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)。
    
## <a name="see-also"></a>另請參閱
 [設定此功能套件](../core/configure-the-feature-pack.md)
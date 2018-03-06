---
title: "追蹤資料至 Application Insights 或事件中心 |Microsoft 文件"
description: "若要啟用分析追蹤資料與 Azure Application Insights 或 BizTalk Server 中的 Azure 事件中心的功能套件的安裝"
ms.custom: fp1, fp2
ms.date: 11/16/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3ff6cb9-44d0-46cd-9b4f-a346365afb7b
caps.latest.revision: 
author: tordgladnordahl
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5ddd60f72955c7196edfc8bf2310b73226d2abe
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="send-biztalk-tracking-data-to-azure-application-insights-or-event-hubs"></a>傳送 BizTalk 追蹤資料到 Azure Application Insights 或事件中心

**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，您可以處理，並將您的追蹤資料傳送至 Azure Application Insights。 
          
**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]功能套件 2**:

* Application Insights 支援 SQL 預設執行個體和具名執行個體的 SQL
* 您可以處理，並將追蹤資料傳送至 Azure 事件中樞

您可以使用這些 Azure 服務，從接收埠、 傳送埠和協調流程追蹤您的執行個體。

## <a name="prerequisites"></a>필수 구성 요소
* 建立的新執行個體[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-create-new-resource)。 BizTalk Server 會使用**檢測金鑰**來驗證。
* 建立[Azure 事件中樞命名空間和事件中樞](https://docs.microsoft.com/azure/event-hubs/event-hubs-create)。 BizTalk Server 會使用 SAS （命名空間層級） 或事件中心層級的原則來驗證。
* 安裝[功能套件 2](https://aka.ms/bts2016fp2)上您 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]

## <a name="enable-analytics-for-your-environment"></a>啟用分析為您的環境

1. 開啟**BizTalk Server 管理**主控台中，以滑鼠右鍵按一下**BizTalk 群組**，然後選取**設定**。 
2. 請檢查**啟用群組層級分析**。
3. 如**目標類型**，選取**Application Insight**或**事件中心**從清單中。
    ![啟用分析為您的環境](../core/media/environmentsettingapplicationinishgt.PNG)

4. 如**連接參數**，選取**...**  按鈕，和**登入**到您的 Azure 帳戶。  

    **Application insights**  
    選取您**訂用帳戶**，**資源群組**，和您的 Application Insights 執行個體。

    ![啟用分析為您的環境](../core/media/analytics-group-application-insights.png)

    **事件中樞**  
    選取您**訂用帳戶**，**資源群組**，事件中樞命名空間，與事件中心。 進行驗證，您可以使用在命名空間層級或在事件中心層級的實體簽章的存取簽章 (SAS)。 可用的索引鍵與先前設定內的值是 自動填入[Azure](https://portal.azure.com)。

    ![啟用分析為您的環境](../core/media/send-tracking-data-to-azure.png)

5. 選取 **確定** 以儲存變更。 

一旦啟用[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]已準備好傳送您的 Azure 資源的資料。 接下來，啟用您的連接埠和協調流程上的分析。 

## <a name="enable-analytics-on-your-artifacts"></a>啟用您的成品上的分析

1. 在 BizTalk Server 管理，以滑鼠右鍵按一下**接收埠**，**傳送埠**或**協調流程**，然後選取**追蹤**。
2. 在下**分析**，檢查**啟用分析**，類似於下列。 這項設定會啟動追蹤和傳輸您的 Azure 資源成品的資料。
    
    ![協調流程的追蹤資料](../core/media/orchestrationsettingsapplicationinsight.PNG)

3. 選取 **確定** 以儲存變更。
4. 重新啟動追蹤主控件執行個體，並確認 BizTalk 應用程式已啟動。

> [!TIP]
> 若要深入組織資料的更多其他系統連接 BizTalk Server 的分析。

## <a name="view-your-data"></a>檢視您的資料

#### <a name="use-application-insights"></a>使用 Application Insights
一旦將資料傳送至 Application Insights，您可以使用在 Azure 中的分析工具來建立進階的查詢、 及分析您的資料。

1. 登入[Azure 入口網站](https://portal.azure.com)。
2. 開啟 Application Insights 資源，並選取**計量瀏覽器**。
3. 空白圖表可能會顯示。 在圖表中，選取**編輯**。 在下**度量**，選取**自訂**若要查看可用的追蹤的屬性。 選取 [一些] 才能看到這些變更在圖表上的不同選項： 

    ![Azure Analytics](../core/media/azure-stream-metrics-custom.png)

4. 返回您的 Application Insights 資源，並選取**分析**。 在**使用量**，選取**執行**。 範例查詢會執行，而且結果會顯示在圖表中。  

> [!TIP]
> Azure 的 Application Insights 是功能強大的工具。 沒有可協助您撰寫查詢，在 Application Insights 中的資源[Application Insights 中的分析](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)，以及甚至開始在[Application Insights 是什麼？](https://docs.microsoft.com/azure/application-insights/app-insights-overview)。

#### <a name="use-event-hubs"></a>使用事件中心
一旦將資料傳送至事件中心時，有幾種方式，以查看資料。 許多事件中心的使用者都使用事件中心擷取資料流的資料載入至 Azure。 目的是讓您將重點放在資料處理，而不是在資料擷取。 [事件中心擷取](https://docs.microsoft.com/azure/event-hubs/event-hubs-capture-overview)說明運作方式以及如何加以設定。

另一個選項是建立接收埠和接收位置使用事件中樞配接器。 然後，您可以將資料輸出至資料夾。 這個概念是如果您想要測試的案例。 [事件中心配接器](event-hubs-adapter.md)列出 BizTalk server 從事件中心接收訊息的步驟。

## <a name="where-the-data-is-stored"></a>儲存資料

將追蹤資料應該相當快速 （在幾分鐘） 內會顯示在您的 Azure 資源。 如果沒有，則有可能發生問題的追蹤主控件。 在 SQL Server 中，分析資料儲存在 BizTalkMsgBoxDb 資料庫中，在 TrackingData_2_*x*資料表。 在 SQL Server Management Studio，傳回這些四個資料表中的前 1000 個資料列。 如果是有資料，然後追蹤主控件不將資料移到 BizTalkDTADb 資料庫。 

一些可能的解決方式：

1. 重新啟動追蹤主控件。
2. 建立專用的追蹤主控件。 安裝 BizTalk Server 時，可能會在啟用追蹤**BizTalk Server 應用程式 1**主機。 一般而言，此應用程式也會用來處理訊息。 建立專用的追蹤主控件使用下列步驟： 

    1. 在 BizTalk Server 管理中，開啟 BizTalk Server 應用程式 1 主控件的屬性，然後取消核取**允許主控件追蹤**。 重新啟動此主控件執行個體。

    2. 建立新的主機名稱為**追蹤**，並檢查**允許主控件追蹤**。 建立主控件執行個體，並將它啟動。

現在，再次查詢 BizTalkMsgBoxDb TrackingData_2_x 資料表。 如果資料表是空的資料移動，而且應該開始在 Application Insights 中顯示。
    
## <a name="see-also"></a>另請參閱
 [安裝及設定此功能套件](../core/configure-the-feature-pack.md)
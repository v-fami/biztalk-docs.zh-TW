---
title: "使用事件中心配接器 |Microsoft 文件"
description: "傳送和接收 BizTalk Server 中使用 Azure 事件中心配接器的訊息"
ms.custom: 
ms.date: 11/16/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: MandiOhlinger
ms.author: plarsen
manager: anneta
ms.openlocfilehash: f394665a40b0a786ef6411b68ff8871e1a683614
ms.sourcegitcommit: f65e8ed2b8c18cded26b9d60868fb6a56bcc1205
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="event-hub-adapter-in-biztalk"></a>事件中樞的配接器在 BizTalk 中

## <a name="overview"></a>概觀
**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]Feature Pack 2**，您可以傳送和接收 BizTalk Server 和 Azure 事件中心之間的訊息。 

Azure 事件中心是可高度擴充的資料流的平台，並可以接收和處理數百萬個每秒的事件。 [事件中心是什麼？](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)提供更多詳細資料。

## <a name="prerequisites"></a>必要條件

* 建立[Azure 事件中樞命名空間和事件中心](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-create)
* 建立[與容器的 Azure blob 儲存體帳戶](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account)
* 安裝[功能套件 2](https://aka.ms/bts2016fp2) BizTalk 伺服器上

現在建立事件中樞，並具有您要傳送與接收事件的連接字串。

## <a name="send-messages-to-event-hubs"></a>將訊息傳送至事件中心

1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，選取**新增**，然後選取**靜態單向傳送埠**。

    [建立傳送埠](../core/how-to-create-a-send-port2.md)提供一些指引。

2. 輸入**名稱**。 在**傳輸**，將**類型**至**EventHub**，然後選取**設定**。 

3. 設定**Azure 帳戶**屬性： 

    |使用|動作|  
    |---|---|  
    | **登入** | 登入您的 Azure 帳戶 |
    | **訂閱** | 選取具有您 EventHubs 命名空間的訂用帳戶 |
    | **資源群組** | 選取您已將 EventHubs 命名空間的資源群組 |

4. 設定**端點**屬性： 

    |使用|動作|  
    |---|---|  
    | **命名空間** | 選取您的事件中樞命名空間，這不是像 sb: / /*youreventhubnamespace*.servicebus.windows.net/ |
    | **名稱** | 選取 （這建立事件中樞命名空間內） 事件中樞的名稱 |
    | **預設資料分割索引鍵** | 選擇性。 [事件中心程式設計指南](https://docs.microsoft.com/azure/event-hubs/event-hubs-programming-guide)上此金鑰提供更多詳細資料。 |
    | **驗證** | **命名空間的存取簽章**是預設值，並會自動使用 RootManageSharedAccessKey 時建立事件中樞命名空間所建立。<br/><br/>**實體的存取簽章**是 SAS 原則，您可以建立事件中心層級 （沒有事件中樞命名空間層級）。 <br/><br/>[事件中心功能概觀](https://docs.microsoft.com/azure/event-hubs/event-hubs-features)更多說明。 |

    完成時，您的內容看起來如下所示： 

    ![端點屬性](../core/media/event-hub-endpoint-properties.png)


5. 選擇性。 設定**訊息**屬性。 **使用者定義的訊息屬性的命名空間**值代表 BizTalk 訊息結構描述對應到事件中心的訊息屬性。

6. 選取**確定**以儲存變更。 


### <a name="test-your-send-port"></a>測試您的傳送埠

您可以使用簡單 File 接收埠和傳送訊息給您的 Azure 事件中心的位置。 

1. 建立使用 File 配接器的接收埠。 內您接收位置，設定**接收資料夾**至 **C:\Temp\In\**，並將檔案遮罩設定為 **\*.xml**。
2. 事件中樞的傳送埠的屬性，設定**篩選**至`BTS.ReceivePortName == FileReceivePort`。
3. 將下列貼到文字編輯器中，並將檔案儲存為**EventHubMessage.xml**。 這是範例訊息。 

    ```xml
    <Data>
      <DataID>DataID_0</DataID>
      <DataDetails>DataDetails_0</DataDetails>
    </Data>
    ```

4. 啟動檔案接收位置和事件中心傳送埠。
5. 複製**EventHubMessage.xml**範例訊息至接收資料夾 (C:\Temp\In\)。 傳送埠傳送到事件中心的 XML 檔案。

## <a name="receive-messages-from-event-hubs"></a>從事件中心接收訊息

1. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**接收埠**，選取**新增**，然後選取**單向接收埠**。 

    [建立接收埠](../core/how-to-create-a-receive-port.md)提供一些指引。

2. 輸入名稱，然後選取**接收位置**。 

3. 選取**新增**，和**名稱**接收位置。 在**傳輸**，選取**EventHub**從**類型**下拉式清單，然後選取**設定**。 

4. 設定**Azure 帳戶**屬性： 

    |使用|動作|  
    |---|---|  
    | **登入** | 登入您的 Azure 帳戶 |
    | **訂閱** | 選取具有您 EventHubs 命名空間的訂用帳戶 |
    | **資源群組** | 選取您已將 EventHubs 命名空間的資源群組 |

4. 設定**端點**屬性： 

    |使用|動作|  
    |---|---|  
    | **命名空間** | 選取您的事件中樞命名空間，這不是像 sb: / /*youreventhubnamespace*.servicebus.windows.net/ |
    | **名稱** | 選取 （這建立事件中樞命名空間內） 事件中樞的名稱 |
    | **取用者群組** | 選取事件中心內的取用者群組。 預設群組會自動建立。 <br/><br/>[事件中心功能概觀](https://docs.microsoft.com/azure/event-hubs/event-hubs-features)提供更多詳細資料。 |
    | **驗證** | **命名空間的存取簽章**是預設值，並會自動使用 RootManageSharedAccessKey 時建立事件中樞命名空間所建立。<br/><br/>**實體的存取簽章**是 SAS 原則，您可以建立事件中心層級 （沒有事件中樞命名空間層級）。 <br/><br/>[事件中心功能概觀](https://docs.microsoft.com/azure/event-hubs/event-hubs-features)更多說明。 |

    完成時，您的內容看起來如下所示： 

    ![端點屬性](../core/media/event-hub-endpoint-receive-properties.png)

5. 設定**檢查點**屬性。 此配接器會使用 Azure blob 儲存體帳戶，能夠可靠地讀取事件使用檢查點，然後再繼續重新啟動。 

    **存放裝置驗證**   
    選取驗證方法。 一般而言，建議使用共用存取簽章。 下列連結是良好的資源，可協助您決定何者最適合您的案例：<br/><br/>[關於 Azure 儲存體帳戶](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account)<br/>[使用共用的存取簽章 (SAS)](https://docs.microsoft.com/azure/storage/common/storage-dotnet-shared-access-signature-part-1)

    完成時，您的內容看起來如下所示： 

    ![檢查點內容](../core/media/event-hub-receive-checkpoint.png)

6. 設定**訊息**屬性： 

    |使用|動作|  
    |---|---|  
    | **命名空間，使用者定義訊息屬性** | http://schemas.microsoft.com/BizTalk/EventHubAdapter/EventData/User 是預設的結構描述，但您可以輸入另一個結構描述。 這個值代表 BizTalk 訊息結構描述對應到事件中心的訊息屬性。 |
    | **使用者定義屬性升級** | 選擇性。 如果您想要的話，您可以升級這些屬性。 <br/><br/>**注意**<br/>需要升級的屬性應有 porperty 結構描述部署*之前*接收事件。|

7. 選取**確定**以儲存變更。 

### <a name="test-your-receive-settings"></a>測試您接收設定

您可以使用簡單的 File 傳送埠從您的 Azure 事件中心接收訊息。 

1. 建立使用 File 配接器的傳送埠。 在傳送埠的屬性，設定**目的地資料夾**至 **C:\Temp\Out\**，並將設定和**檔案名稱**至**%MessageID%.xml**.
2. 在您的檔案傳送埠的屬性，設定**篩選**至`BTS.ReceivePortName == EHReceivePort`。
3. 開始事件中心接收位置和 File 傳送埠。
4. 尋找目的地資料夾 (c:\temp\out) 中的訊息。

## <a name="do-more"></a>執行其他動作
事件中心會被視為 「 前端 」 很多的其他 Azure 服務，包括 Azure 資料湖、 HD Insight 等等。 它被設計來處理大量訊息，並處理它們更快速。 深入了解事件中心和其功能： 

[事件中心功能概觀](https://docs.microsoft.com/azure/event-hubs/event-hubs-features)  
[事件中心是什麼？](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)
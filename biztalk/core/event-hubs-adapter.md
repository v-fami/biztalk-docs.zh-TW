---
title: 使用事件中樞配接器 |Microsoft Docs
description: 傳送和接收 BizTalk Server 中使用 Azure 事件中樞配接器的訊息
ms.custom: ''
ms.date: 11/16/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: MandiOhlinger
ms.author: plarsen
manager: anneta
ms.openlocfilehash: a1e30b1ab1aacc1c5134d1dd5b44744bd670b308
ms.sourcegitcommit: c3070a7a3f332857357f056dc632829b43869c17
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2018
ms.locfileid: "51630331"
---
# <a name="event-hub-adapter-in-biztalk"></a>在 BizTalk 中的事件中樞配接器

## <a name="overview"></a>總覽
**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]Feature Pack 2**，您可以傳送和接收 BizTalk Server 和 Azure 事件中樞之間的訊息。 

Azure 事件中樞是可高度擴充的資料串流平台，並可接收和處理數百萬個每秒的事件。 [事件中樞是什麼？](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)提供更多詳細資料。

## <a name="prerequisites"></a>先決條件

* 建立[Azure 事件中樞命名空間和事件中樞](https://docs.microsoft.com/azure/event-hubs/event-hubs-create)
* 建立[與容器的 Azure blob 儲存體帳戶](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account)
* 安裝[Feature Pack 2](https://aka.ms/bts2016fp2) BizTalk 伺服器上

現已建立事件中樞，並已傳送和接收事件所需的連接字串。

## <a name="send-messages-to-event-hubs"></a>將訊息傳送至事件中樞

1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，選取**新增**，然後選取**靜態單向傳送埠**。

    [建立傳送埠](../core/how-to-create-a-send-port2.md)提供一些指引。

2. 請輸入**名稱**。 在**傳輸**，將**型別**來**EventHub**，然後選取**設定**。 

3. 設定**Azure 帳戶**屬性： 

    |使用|動作|  
    |---|---|  
    | **登入** | 登入您的 Azure 帳戶 |
    | **訂閱** | 選取具有您 EventHubs 命名空間的訂用帳戶 |
    | **資源群組** | 選取您已將 EventHubs 命名空間的資源群組 |

4. 設定**端點**屬性： 

    |使用|動作|  
    |---|---|  
    | **Namespace** | 選取事件中樞命名空間，也就是類似 sb: / /*youreventhubnamespace*.servicebus.windows.net/ |
    | **名稱** | 選取事件中樞 （這建立事件中樞命名空間內） 的名稱 |
    | **預設資料分割索引鍵** | 選擇性。 [事件中樞程式設計指南](https://docs.microsoft.com/azure/event-hubs/event-hubs-programming-guide)此金鑰提供更多詳細資料。 |
    | **驗證** | **命名空間存取簽章**是預設值，並會自動使用 [RootManageSharedAccessKey] 時建立事件中樞命名空間所建立。<br/><br/>**實體存取簽章**是在事件中樞層級 （非事件中樞命名空間層級），您可以建立 SAS 原則。 <br/><br/>[事件中樞功能概觀](https://docs.microsoft.com/azure/event-hubs/event-hubs-features)說明更多。 |

    完成時，您的屬性看起來如下所示： 

    ![端點屬性](../core/media/event-hub-endpoint-properties.png)


5. 選擇性。 設定**訊息**屬性。 **使用者定義的訊息屬性的命名空間**值代表 BizTalk 訊息的結構描述，對應至事件中樞的訊息屬性。

6. 選取  **Ok**以儲存變更。 


### <a name="test-your-send-port"></a>測試您的傳送埠

您可以使用簡單檔案接收埠，並將訊息傳送至您的 Azure 事件中樞的位置。 

1. 建立使用 File 配接器的接收埠。 內您接收位置，設定**接收資料夾**要**C:\Temp\In\\**，並將檔案遮罩設定為 **\*.xml**。
2. 在事件中樞將傳送埠屬性，設定**篩選條件**至`BTS.ReceivePortName == FileReceivePort`。
3. 將下列內容貼入文字編輯器，並將檔案儲存為**EventHubMessage.xml**。 這是您的範例訊息。 

    ```xml
    <Data>
      <DataID>DataID_0</DataID>
      <DataDetails>DataDetails_0</DataDetails>
    </Data>
    ```

4. 啟動檔案接收位置和事件中樞傳送埠。
5. 複製**EventHubMessage.xml**範例訊息至接收資料夾 (C:\Temp\In\)。 傳送埠會將 XML 檔案傳送到事件中樞。

## <a name="receive-messages-from-event-hubs"></a>從事件中樞接收訊息

1. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**接收連接埠**，選取**新增**，然後選取**單向接收埠**。 

    [建立接收埠](../core/how-to-create-a-receive-port.md)提供一些指引。

2. 輸入名稱，然後選取**接收位置**。 

3. 選取 **的新**，並**名稱**接收位置。 在 **傳輸**，選取**EventHub**從**型別**下拉式清單，然後選取**設定**。 

4. 設定**Azure 帳戶**屬性： 

    |使用|動作|  
    |---|---|  
    | **登入** | 登入您的 Azure 帳戶 |
    | **訂閱** | 選取具有您 EventHubs 命名空間的訂用帳戶 |
    | **資源群組** | 選取您已將 EventHubs 命名空間的資源群組 |

4. 設定**端點**屬性： 

    |使用|動作|  
    |---|---|  
    | **Namespace** | 選取事件中樞命名空間，也就是類似 sb: / /*youreventhubnamespace*.servicebus.windows.net/ |
    | **名稱** | 選取事件中樞 （這建立事件中樞命名空間內） 的名稱 |
    | **取用者群組** | 選取事件中樞內的取用者群組。 會自動建立預設群組。 <br/><br/>[事件中樞功能概觀](https://docs.microsoft.com/azure/event-hubs/event-hubs-features)提供更多詳細資料。 |
    | **驗證** | **命名空間存取簽章**是預設值，並會自動使用 [RootManageSharedAccessKey] 時建立事件中樞命名空間所建立。<br/><br/>**實體存取簽章**是在事件中樞層級 （非事件中樞命名空間層級），您可以建立 SAS 原則。 <br/><br/>[事件中樞功能概觀](https://docs.microsoft.com/azure/event-hubs/event-hubs-features)說明更多。 |

    完成時，您的屬性看起來如下所示： 

    ![端點屬性](../core/media/event-hub-endpoint-receive-properties.png)

5. 設定**檢查點**屬性。 此配接器會使用 Azure blob 儲存體帳戶，可靠地讀取事件使用檢查點，然後再繼續重新啟動。 

    **存放裝置驗證**   
    選取驗證方法。 一般而言，建議使用共用存取簽章。 下列連結是不錯的資源，可協助您決定何者最適合您的案例：<br/><br/>[關於 Azure 儲存體帳戶](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account)<br/>[使用共用的存取簽章 (SAS)](https://docs.microsoft.com/azure/storage/common/storage-dotnet-shared-access-signature-part-1)

    完成時，您的屬性看起來如下所示： 

    ![檢查點內容](../core/media/event-hub-receive-checkpoint.png)

6. 設定**訊息**屬性： 

    |使用|動作|  
    |---|---|  
    | **命名空間，使用者定義訊息屬性** |  `http://schemas.microsoft.com/BizTalk/EventHubAdapter/EventData/User` 預設結構描述中，但您可以輸入另一個結構描述。 這個值代表 BizTalk 訊息的結構描述，對應至事件中樞的訊息屬性。 |
    | **升級使用者定義的屬性** | 選擇性。 如果您想，您可以升級這些屬性。 <br/><br/>**注意**<br/>要升級的屬性應該部署的 porperty 結構描述*之前*接收事件。|

7. 選取  **Ok**以儲存變更。 

### <a name="test-your-receive-settings"></a>測試您接收設定

您可以使用簡單的 File 傳送埠以接收來自 Azure 事件中樞的訊息。 

1. 建立使用 File 配接器的傳送埠。 在您傳送連接埠的屬性，設定**目的地資料夾**要**C:\Temp\Out\\**，並設定和**檔案名稱**至 **%MessageID%.xml**.
2. 在您的檔案傳送埠屬性，設定**篩選條件**至`BTS.ReceivePortName == EHReceivePort`。
3. 開始事件中樞接收位置和 File 傳送埠。
4. 尋找目的地資料夾 (c:\temp\out) 中的訊息。

## <a name="do-more"></a>執行更多作業
事件中樞會被視為 「 前端 」 許多其他 Azure 服務，包括 Azure Data Lake、 HD Insight 和更多功能。 它被設計來處理許多訊息，並加以處理快速。 深入的了解事件中樞，以及其功能： 

[事件中樞功能概觀](https://docs.microsoft.com/azure/event-hubs/event-hubs-features)  
[事件中樞是什麼？](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)

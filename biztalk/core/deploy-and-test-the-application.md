---
title: "部署和測試應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2c86d5f-1849-4b7d-8061-23f156245f5b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56b390ef87ac2ea58d91be2ff16a50f2c3748db2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deploy-and-test-the-application"></a>部署和測試應用程式
> [!NOTE]
>  本教學課程僅適用於 [!INCLUDE[prague](../includes/prague-md.md)]。  
  
 本主題中，我們建置、 部署、 設定及測試[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。  
  
## <a name="build-and-deploy-the-application"></a>建置和部署應用程式  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案名稱，然後**屬性**。  
  
2.  在 屬性頁面上，按一下 簽署 索引標籤，選取 簽署組件 核取方塊，，從下拉式清單選擇建立新的強式名稱金鑰檔案的選項。 遵循提示來建立檔案。  
  
3.  將變更儲存至專案。 在 [方案總管] 中，以滑鼠右鍵按一下方案名稱，然後**建置方案**。  
  
4.  專案建置成功之後，在 [方案總管] 中，以滑鼠右鍵按一下方案名稱，然後按一下**部署方案**。  
  
## <a name="configure-the-application"></a>設定應用程式  
 在 設定應用程式，[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]建立傳送和接收埠，然後將它們繫結至協調流程和邏輯傳送/接收埠建立協調流程的一部分。  
  
1.  建立接收埠所接收 JSON 訂單會透過[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。  
  
    1.  在[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk Application 1**，以滑鼠右鍵按一下**接收埠**，指向**新增**，然後按一下 **單向接收埠**.  
  
    2.  提供接收埠名稱，然後再從左邊的移動瀏覽，按一下**接收位置**。 在**接收位置**索引標籤上，按一下 **新增**。  
  
    3.  指定接收位置的名稱，請選取連接埠類型為**檔案**，然後按一下 **設定**。  
  
    4.  提供的資料夾位置，從接收位置選取內送的 JSON 訂單的地方。 指定`*.json`作為檔案遮罩，然後按一下**確定**。  
  
    5.  從**接收管線**下拉式清單中，選取**JSONToXml**。 建立此自訂接收管線[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。 以滑鼠右鍵按一下省略符號**（...）**按鈕旁至管線，然後在之下**階段 1 – Deocde 元件**，提供下列值：  
  
        -   根節點-`ROOT`  
  
        -   RootNodeNamespace –`http://BTSJSON`。  
  
         這些值代表目標命名空間和 XML 採購單結構描述所產生 JSON 採購訂單使用 JSON 結構描述精靈中的根節點名稱。  
  
    6.  按一下**確定**直到結束所有開啟的對話方塊。  
  
2.  建立傳送埠傳送出 JSON 發票訊息。  
  
    1.  在[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk Application 1**，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 **靜態的單向傳送埠**.  
  
    2.  指定傳送埠的名稱，請選取連接埠類型為**檔案**，然後按一下 **設定**。  
  
    3.  提供傳送埠要將複製的連出 JSON 發票的資料夾位置。 指定`%MessageID%.json`做為檔案名稱，然後按一下**確定**。  
  
    4.  從**傳送管線**下拉式清單中，選取**XmlToJSON**，然後按一下 **確定**。  
  
    5.  按一下**確定**直到結束所有開啟的對話方塊。  
  
3.  最後，繫結的邏輯連接埠，您建立的實際協調流程連接埠，您現在可以設定應用程式。  
  
    1.  以滑鼠右鍵按一下**BizTalk Application 1**，然後按一下 **設定**。  
  
    2.  從左窗格中，按一下  **ProcessPO**。 從右窗格中，關聯[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]裝載，將邏輯連接埠對應到實體連接埠，然後按**確定**。  
  
    3.  以滑鼠右鍵按一下**BizTalk Application 1**，然後按一下 **啟動**。  
  
## <a name="test-the-application"></a>測試應用程式  
  
1.  瀏覽至您下載時，此範例中，且從**TestMessage**資料夾，複製**JsonPurchaseOrder.json**，並將它貼入您與接收位置相關聯的資料夾中。 等候檔案消失時。  
  
2.  瀏覽至您與您所建立的傳送埠相關聯的資料夾。 請注意，   ***\<GUID >*.json**檔案位於資料夾中。 開啟檔案，並確認它是發票訊息。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk Server 處理 JSON 訊息](../core/processing-json-messages-using-biztalk-server.md)
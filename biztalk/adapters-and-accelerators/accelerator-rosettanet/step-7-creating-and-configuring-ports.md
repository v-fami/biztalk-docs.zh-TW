---
title: "步驟 7： 建立及設定連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private process tutorial, creating ports
- private process tutorial, configuring ports
ms.assetid: c00344c6-506a-4560-a948-e5fed2b9fd58
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44a9696f907928f31a740e4d8545567921a82df9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-7-creating-and-configuring-ports"></a>步驟 7： 建立及設定連接埠
在這個步驟中，您會建立和設定與商務程序進行通訊所使用的連接埠。 每一個連接埠都有類型、方向和繫結等屬性， 分別指定通訊的方向和模式、訊息的傳送或接收位置、以及通訊的進行方式。  
  
### <a name="to-create-a-logical-send-port"></a>建立邏輯傳送埠  
  
1.  在 Visual Studio 中，從 [工具箱] 拖曳**連接埠**圖形至協調流程設計介面並將它放在**連接埠介面**開啟**連接埠組態精靈**。  
  
2.  在**連接埠組態精靈**頁面上，按一下**下一步**。  
  
3.  在**連接埠內容**頁面上，於**名稱**方塊中，輸入**ContosoSQLReqResponsePort**，然後按一下 **下一步**。  
  
4.  在**選取連接埠類型**頁面上，於**連接埠類型名稱**方塊中，輸入**ContosoSQLReqResponsePortName**。  
  
5.  如**通訊模式**，選取**要求-回應**。  
  
6.  如**存取限制**，選取**內部-限制於此專案**，然後按一下 **下一步**。  
  
7.  在**連接埠繫結**頁面上，選取**我要傳送要求並接收回應**，保留**連接埠繫結**選項設定為**稍後指定**，然後按一下 **下一步**。  
  
8.  按一下**完成**建立連接埠。  
  
### <a name="to-change-the-variable-type-for-the-orchestration-ports"></a>變更協調流程連接埠的變數類型  
  
1.  在協調流程 檢視中，展開**類型**，依序展開**連接埠類型**，依序展開**ContosoSQLReqResponsePortName**，依序展開**Operation_1**，然後選取**要求**。  
  
2.  在 屬性 視窗中，選取**訊息類型**屬性中，展開**結構描述**，然後按一下  **\<從參考組件選取\>**.  
  
3.  在 選取成品類型 對話方塊中，按一下  **ContosoPriceAndAvailability**。  
  
4.  在右窗格中，選取**rootPriceRequest**，然後按一下 **確定**。  
  
5.  在協調流程檢視下**Operation_1**，選取**回應**如**ContosoSQLReqResponsePortName**連接埠類型。  
  
6.  在 屬性 視窗中，選取**訊息類型**屬性中，展開**結構描述**，然後按一下  \<**從參考組件選取\>**.  
  
7.  在**選取成品類型**對話方塊中，按一下  **ContosoPriceAndAvailability**。  
  
8.  在右窗格中，選取**rootPriceResponse**，然後按一下 **確定**。  
  
### <a name="to-connect-the-ports-to-the-receive-shapes"></a>連接連接埠和接收圖形  
  
1.  協調流程設計介面上，選取**[send_1]**圖形。  
  
2.  在 [屬性] 視窗中，選取**訊息**屬性，然後再選取**Contoso3A2RequestMessage**從下拉式清單。  
  
3.  連接**ContosoSQLReqResponsePort**旁的 選取的綠色控點**要求**標籤，並將它拖曳上的綠色控點**send_1**圖形。  
  
4.  協調流程設計介面上，選取**Receive_1**圖形。  
  
5.  在 [屬性] 視窗中，選取**訊息**屬性，然後再選取**Contoso3A2ResponseMessage**從下拉式清單。  
  
6.  連接**ContosoSQLReqResponsePort**旁的 選取的綠色控點**回應**標籤，並將它拖曳上的綠色控點**Receive_1**圖形。  
  
7.  在**檔案**功能表上，按一下 **全部儲存**。  
  
## <a name="see-also"></a>請參閱  
 [步驟 8：建立與部署 Contoso 協調流程](../../adapters-and-accelerators/accelerator-rosettanet/step-8-building-and-deploying-the-contoso-orchestration.md)
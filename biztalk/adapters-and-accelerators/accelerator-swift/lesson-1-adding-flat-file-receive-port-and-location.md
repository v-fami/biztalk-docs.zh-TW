---
title: 第 1 課： 加入一般檔案接收埠和位置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive locations, creating
- creating, receive locations
- receive ports, creating
- creating, receive ports
ms.assetid: 881f58d8-f541-4a85-b534-cb1ca627c002
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e23525715be1816684ffa680f99cf8f8bd88ceca
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966263"
---
# <a name="lesson-1-adding-flat-file-receive-port-and-location"></a>第 1 課： 新增一般檔案接收埠和位置
接收埠一律會有新增接收埠時，您必須設定相關聯的接收位置。 接收位置定義內送訊息和管線，您用來處理訊息的特定位址。  
  
### <a name="to-add-a-receive-port"></a>新增接收埠  
  
1. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**。  
  
2. 在接收埠屬性 對話方塊中，在**名稱**方塊中，輸入**MT103_FlatFile_ReceivePort**。  
  
3. 按一下 **套用**要繫結連接埠，然後按一下**確定**。  
  
4. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**接收位置**，指向**新增**，然後按一下**單向接收位置**。  
  
5. 在 [選取接收埠] 對話方塊中，按一下**MT103_FlatFile_ReceivePort**，然後按一下**確定**。  
  
6. 在 [接收位置屬性] 對話方塊中，在**名稱**方塊中，輸入**MT103_FlatFile_ReceiveLocation**。  
  
7. 在**傳輸**區段中，如**型別**文字方塊中，按一下下拉式清單中，然後按**檔案**。  
  
8. 按一下 **設定**按鈕右邊的 類型 下拉式清單。  
  
9. 在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。  
  
10. 在 [瀏覽資料夾] 對話方塊中，移至**\<磁碟機\>: \Labs\Inbound**資料夾，然後再按一下**建立新資料夾**。  
  
11. 建立**FlatFile**中的資料夾**\<磁碟機\>: \Labs\Inbound**，然後按一下**確定**。  
  
12. 在 **檔案遮罩**方塊中，輸入 **\*.txt**，然後按一下 **確定**。  
  
13. 在 接收位置屬性 對話方塊中，確定**BizTalkServerApplication**輸入**接收處理常式** 方塊中。  
  
14. 針對**接收管線**方塊中，選取**MT103ReceivePipeline**從下拉式清單。  
  
15. 按一下 **套用**，然後按一下**確定**。  
  
16. 在 BizTalk Server 管理主控台中，按一下**接收位置**，以滑鼠右鍵按一下**MT103_FlatFile_ReceiveLocation**，然後按一下**啟用**。  
  
    請繼續進行[第 2 課： 新增 XML 傳送埠](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-an-xml-send-port.md)。
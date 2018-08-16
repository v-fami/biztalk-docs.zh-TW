---
title: 第 2 課： 加入一般檔案傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send ports, flat files
- flat files, send ports
- creating, send ports
- send ports, creating
ms.assetid: 33dceb0d-85f5-4e19-820f-cd33b60cd32a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90b08dd8083e78d1e7cd98e8e8f705ac23d9bd17
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997319"
---
# <a name="lesson-2-adding-a-flat-file-send-port"></a>第 2 課： 加入一般檔案傳送埠
在這一課，您可以設定傳送埠和傳送位置。 您可以使用傳送埠定義您想要傳送訊息的方式。 您也會建立傳送訊息的檔案資料夾位置。  

### <a name="to-add-a-flat-file-send-port"></a>若要新增一般檔案傳送埠  

1. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態單向傳送埠**。  

2. 在傳送埠屬性 對話方塊中，在**名稱**方塊中，輸入**MT103_FlatFile_SendPort**。  

3. 在**傳輸**區段中，如**型別**方塊中，按一下下拉式清單中，並選取**檔案**。  

4. 按一下 **設定**按鈕右邊的 類型 下拉式清單。  

5. 在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。  

6. 在 [瀏覽資料夾] 對話方塊中，移至**\<磁碟機\>: \Labs**資料夾，然後再按一下**建立新資料夾**。  

7. 建立**Outbound**資料夾中的**\<磁碟機\>: \Labs**，然後按一下**確定**。  

8. 在 **檔名**方塊中，輸入 **%MessageID%.txt**，然後按一下  **確定**。  

9. 在傳送埠屬性 對話方塊中，按一下下拉式清單，如**傳送管線**方塊，然後按**MT103SendPipeline**。  

10. 在左窗格中，按一下**篩選**，然後執行下列操作：  


    |   使用   |           以進行此動作            |
    |--------------|---------------------------------|
    | **屬性** | 選取**BTS。ReceivePortName**。 |
    | **[運算子]** |         選取  **==**。          |
    |  **ReplTest1**   | 型別**MT103_XML_ReceivePort**。 |


11. 按一下 **套用**，然後按一下  **確定。**  

12. 在 **傳送埠** 窗格中，以滑鼠右鍵按一下**MT103_FlatFile_SendPort**，然後按一下 **啟動**。  

    請繼續進行[模組 5： 新增一般檔案接收位置和 XML 傳送埠](../../adapters-and-accelerators/accelerator-swift/module-5-adding-a-flat-file-receive-location-and-xml-send-port.md)。
---
title: 第 2 課： 加入一般檔案傳送埠 |Microsoft 文件
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
ms.openlocfilehash: d438a6fa68136b05b358a81f4b026350d92a6af4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25961332"
---
# <a name="lesson-2-adding-a-flat-file-send-port"></a>第 2 課： 加入一般檔案傳送埠
在這一課，您可以設定傳送埠和傳送位置。 您可以使用傳送埠定義您想要傳送訊息的方式。 您也可以建立傳送訊息的檔案資料夾位置。  
  
### <a name="to-add-a-flat-file-send-port"></a>若要加入一般檔案傳送埠  
  
1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
2.  在 [傳送埠屬性] 對話方塊中**名稱**方塊中，輸入**MT103_FlatFile_SendPort**。  
  
3.  在**傳輸** 區段中，針對**類型**方塊中，按一下下拉式清單，並選取**檔案**。  
  
4.  按一下**設定**按鈕右邊的 [類型] 下拉式清單。  
  
5.  在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。  
  
6.  在 [瀏覽資料夾] 對話方塊中，移至**\<磁碟機\>: \Labs**資料夾，然後再按一下**建立新資料夾**。  
  
7.  建立**輸出**資料夾中的**\<磁碟機\>: \Labs**，然後按一下 **確定**。  
  
8.  在**檔案名稱**方塊中，輸入 **%MessageID%.txt**，然後按一下 **確定**。  
  
9. 在 傳送埠屬性 對話方塊中，按一下 下拉式清單，如**傳送管線**方塊，並選取**MT103SendPipeline**。  
  
10. 在左窗格中，按一下 **篩選**，然後執行下列步驟：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性**|選取**BTS。ReceivePortName**。|  
    |**運算子**|選取 **==** 。|  
    |**值**|型別**MT103_XML_ReceivePort**。|  
  
11. 按一下**套用**，然後按一下  **確定。**  
  
12. 在**傳送埠**] 窗格中，以滑鼠右鍵按一下**MT103_FlatFile_SendPort**，然後按一下 [**啟動**。  
  
 若要繼續[模組 5： 加入一般檔案接收位置和 XML 傳送埠](../../adapters-and-accelerators/accelerator-swift/module-5-adding-a-flat-file-receive-location-and-xml-send-port.md)。
---
title: "新增 MX 傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3ad5d2f-1fcb-49d4-9974-664733308f45
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3cd4c16658ad0ff6b85976fbc6a97c4f397acbdb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adding-an-mx-send-port"></a>新增 MX 傳送連接埠
**若要新增 MX 傳送埠：**  
  
1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
2.  在 傳送埠屬性 對話方塊中，在 名稱方塊中，輸入**MX_SendPort**。  
  
3.  在 [傳輸] 區段的 [類型] 方塊中，按一下下拉式清單，然後**檔案**。  
  
4.  按一下**設定**按鈕右邊的 [類型] 下拉式清單。  
  
5.  在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。  
  
6.  在瀏覽資料夾] 對話方塊中，選取 [檔案位置。  
  
7.  在 檔案名稱 方塊中，輸入**%MessageID%.xml**，然後按一下 **確定**。  
  
8.  在 [傳送埠屬性] 對話方塊中，按一下 [傳送管線] 方塊中的下拉式清單，然後選取傳送管線已部署管線專案中。  
  
9. 在左窗格中，按一下 **篩選**，然後指定下列：  
  
    |||  
    |-|-|  
    |屬性|Microsoft.Solutions.MX_A4SWIFT。Property.MX_A4SWIFT_Failed|  
    |運算子|選取 = =|  
    |值|False|  
  
10. 按一下**套用**，然後按一下 **確定**。  
  
11. 在 傳送埠 窗格中，以滑鼠右鍵按一下**MX_SendPort**，然後按一下 **啟動**。
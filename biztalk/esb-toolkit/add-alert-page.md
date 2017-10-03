---
title: "新增警示 頁面 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0023ee8d-a0d1-4257-95c6-38c95060bd62
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa93a777481c905dbedfffe5e7675335c4aec40b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="add-alert-page"></a>[新增警示] 頁面
圖 1 顯示 新增警示頁面上，您可以在其中建立新的警示在入口網站將會引發當符合警示中指定的準則 （條件） 的錯誤訊息抵達入口網站。  
  
 ![新增警示 頁面](../esb-toolkit/media/ch8-addalertpage.gif "Ch8 AddAlertPage")  
  
 **圖 1**  
  
 **ESB Management 入口網站新增警示 頁面**  
  
 您可以在新增警示 頁面上，執行下列作業：  
  
-   輸入新的警示中的名稱**輸入警示名稱**文字方塊。  
  
-   指定警示將會符合的傳入例外狀況中的欄位值的方式**加入此警示的條件**本頁一節。 從例外狀況的結構描述中選取欄位 (例如**應用程式、 錯誤類型**或**錯誤嚴重性)**中**準則**下拉式清單，選取比較型別 （例如與 =， **！ =、 > =、 < =、**或**像**) 中**運算子**下拉式清單，並輸入或選取第三個清單中的值。 當您選取的例外狀況欄位，**值**控制項變更為 [文字] 方塊或下拉式清單，以輸入或選取相符的值。  
  
-   選取或輸入準則值之後, 按**新增**連結加入到清單中的這種狀況**條件**的頁面上，重複上述步驟，加入任何您需要這項警示的更多條件區段.  
  
-   按一下**儲存**按鈕以建立新的警示名稱與您指定的條件。
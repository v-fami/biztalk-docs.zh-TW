---
title: "新增 MX 接收埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4818d6af-df1d-481e-becf-1af633735248
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69123b876bdda4b5f999277a1710cdeb1cb61fe7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adding-mx-receive-port"></a>新增 MX 接收埠
**新增 MX 接收埠：**  
  
1.  啟動**BizTalk Server 管理**主控台。  
  
2.  在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開  **BizTalk Application 1**。  
  
3.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。  
  
4.  在 [接收埠屬性] 對話方塊的 [名稱] 方塊中輸入**MX_ 接收埠**。  
  
5.  按一下**套用**來繫結連接埠，然後按一下**確定**。  
  
6.  以滑鼠右鍵按一下**接收位置**，指向 **新增**，然後按一下 **單向接收位置**。  
  
7.  在 選取接收埠 對話方塊中，按一下  **MX_ 接收埠**，然後按一下 **確定**。  
  
8.  在 [接收位置屬性] 對話方塊的 [名稱] 方塊中輸入**MX_ 接收位置**。  
  
9. 在 [傳輸] 區段中，類型的文字方塊中，按一下下拉式清單，然後**檔案**。  
  
10. 按一下**設定**按鈕右邊的 [類型] 下拉式清單。  
  
11. 在 FILE 傳輸屬性 對話方塊中，按一下**瀏覽**，然後選取 檔案位置。  
  
12. 在 [FILE 傳輸屬性] 對話方塊中，確定\*.xml 檔案遮罩] 方塊中，輸入，然後按一下 [**確定**。  
  
13. 在 [接收位置屬性] 對話方塊中，確認 [biztalkserverapplication]，輸入接收處理常式方塊。  
  
14. 在接收管線] 方塊中，選取**接收管線**（已部署管線專案中的接收管線） 從下拉式清單中，按一下**套用**，然後按一下 [**確定**.  
  
15. 以滑鼠右鍵按一下您剛才設定，然後再按一下位置**啟用**。
---
title: "如何建立傳送 Port1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating send ports
- send ports, creating
ms.assetid: bf32e9f5-ebed-43d2-b9a9-6ab91925d973
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61c82b199f7b8686556f2cbb53a90b0d4b59536e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-send-port"></a>如何建立傳送埠
使用下列程序建立 JD Edwards EnterpriseOne 的 BizTalk Server 傳送埠。  
  
### <a name="to-create-a-send-port"></a>建立傳送埠  
  
1.  以滑鼠右鍵按一下 [傳送埠] 節點。  
  
2.  按一下**新增傳送埠**。  
  
3.  在**建立新傳送埠**對話方塊中，選取**靜態請求-回應連接埠**從**指定傳送埠類型**清單，然後按**確定**.  
  
     **靜態請求-回應傳送埠屬性**視窗隨即開啟。  
  
4.  輸入傳送埠名稱，例如`SSOSendToJDEEntOne`。  
  
5.  按一下**傳輸**的左窗格中。  
  
6.  按一下**傳輸類型**，然後選取**[jdeentone]**。  
  
7.  選取**位址 (URI)**，然後按一下省略符號 （...） 按鈕。  
  
     JD Edwards EnterpriseOne**傳輸屬性** 對話方塊隨即出現。  
  
8.  型別`myJDEEntOneSSO`如**邏輯系統名稱**。  
  
9. 選取**是**如**使用 SSO**。  
  
10. 在下拉式清單中，選取您建立來代表 JD Edwards EnterpriseOne 系統的單一登入 (SSO) 分支機構應用程式。  
  
     按一下**確定**以確認您輸入的資訊。  
  
## <a name="see-also"></a>另請參閱  
 [建立分支機構應用程式](../core/creating-affiliate-applications4.md)   
 [使用單一登入](../core/using-single-sign-on1.md)
---
title: 第 1 課： 新增 XML 接收埠和位置 |Microsoft Docs
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
ms.assetid: 252bc080-3820-44cc-8749-715869f3f684
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51a6f5665fe460084319401e24090a8e92ea8987
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010231"
---
# <a name="lesson-1-adding-xml-receive-port-and-location"></a>第 1 課： 新增 XML 接收埠和位置
接收埠是相似接收位置的邏輯群組。 接收位置內送訊息，並將用來處理訊息的管線會定義特定位址 （例如 URL 或檔案的位置）。  
  
### <a name="to-add-a-receive-port"></a>新增接收埠  
  
1. 開始**BizTalk Server 管理**主控台。  
  
   > [!NOTE]
   >  BizTalk Server 管理主控台可以也從開啟 Visual Studio 中依序按一下**BizTalk Server 管理**中**工具**功能表。  
  
2. 在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**節點，則**BizTalk 群組**節點，則**應用程式** 節點，然後**BizTalk Application 1**節點。  
  
3. 以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**。  
  
4. 在接收埠屬性 對話方塊中，在**名稱**方塊中，輸入**MT103_XML_ReceivePort**。  
  
5. 按一下 **套用**來繫結連接埠，然後按一下  **確定。**  
  
6. 以滑鼠右鍵按一下**接收位置**，指向**新增**，然後按一下**單向接收位置**。  
  
7. 在 [選取接收埠] 對話方塊中，按一下**MT103_XML_ReceivePort**，然後按一下**確定**。  
  
8. 在 [接收位置屬性] 對話方塊中，在**名稱**方塊中，輸入**MT103_XML_ReceiveLocation**。  
  
9. 在**傳輸**區段中，如**型別**文字方塊中，按一下下拉式清單中，然後按**檔案**。  
  
10. 按一下 **設定**按鈕右邊的 類型 下拉式清單。  
  
11. 在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。 移至**\<磁碟機\>: \Labs**資料夾，然後再按一下**建立新資料夾**。  
  
12. 在瀏覽資料夾 對話方塊中，建立**Inbound**資料夾中的**\<磁碟機\>: \Labs**，然後建立**XMLFile** 資料夾**\<磁碟機\>: \Labs\Inbound**。 按一下 [確定] 。  
  
13. 在 [FILE 傳輸屬性] 對話方塊中，請確認 **\*.xml**中輸入**檔案遮罩**方塊，然後再按一下**確定**。  
  
14. 在 接收位置屬性 對話方塊中，確定**BizTalkServerApplication**輸入**接收處理常式** 方塊中。  
  
15. 針對**接收管線**方塊中，選取**XMLReceive**從下拉式清單。  
  
16. 按一下 **套用**，然後按一下**確定**。  
  
17. 在 BizTalk Server 管理主控台中，按一下**接收位置**，以滑鼠右鍵按一下**MT103_XML_ReceiveLocation**，然後按一下**啟用**。  
  
    > [!NOTE]
    >  啟用接收位置之後，BizTalk 會主動輪詢您檔案的資料夾。  
  
    請繼續進行[第 2 課： 加入一般檔案傳送埠](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-a-flat-file-send-port.md)。
---
title: "建立 A4SWIFT 接收位置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, creating
- creating, receive locations
ms.assetid: 712cf42f-8d71-47e9-b2bf-3da158b74fe4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3f0835c6d83efc9db91f5c1d63e91f4c143399d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-an-a4swift-receive-location"></a>建立 A4SWIFT 接收位置
您必須建立[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收位置，才能啟用訊息接收 SWIFT 網路[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]，如下圖所示。 接收位置接收一般檔案訊息從輸入的檔案資料夾。  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-receive-location-configuration.gif "A4SWIFT_Receive_Location_Configuration")  
  
 **摘要**  
  
 建立和繫結單向接收埠，然後建立並啟用接收位置具有下列屬性和元件：  
  
|屬性/元件|設定|  
|--------------------------|-------------|  
|接收埠|單向連接埠|  
|傳輸類型|FILE|  
|位址的 URI|您想要接收訊息的資料夾名稱|  
|檔案遮罩|\*.*\<副檔名 >*，其中\<*延伸*> 是個內送的延伸模組一般檔案訊息|  
|接收處理常式|BizTalkServerApplication|  
|接收管線|[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收您所建立的管線|  
  
### <a name="to-add-the-receive-port-and-location"></a>若要加入的接收埠和位置  
  
1.  啟動**BizTalk Server 管理**主控台。  
  
    > [!NOTE]
    >  BizTalk Server 管理主控台也可以開啟從 Visual Studio 中依序按一下**BizTalk Server 管理**中**工具**功能表。  
  
2.  在管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開**BizTalk應用程式 1**。  
  
3.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。  
  
4.  在 [接收埠屬性] 對話方塊中**名稱**方塊中，輸入接收埠的名稱。  
  
5.  按一下**套用**來繫結連接埠，然後按一下**確定**。  
  
6.  以滑鼠右鍵按一下**接收位置**，指向 **新增**，然後按一下 **單向接收位置**。  
  
7.  在 [選取接收埠] 對話方塊中，按一下您剛才的接收埠建立，，然後按一下**確定**。  
  
8.  在 [接收位置屬性] 對話方塊中**名稱**方塊中，輸入接收位置的名稱。  
  
9. 在**傳輸** 區段中，針對**類型** 文字方塊中，按一下下拉式清單中，，然後選取**檔案**。  
  
10. 按一下**設定**按鈕右邊的 [類型] 下拉式清單。  
  
11. 在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。 您想要接收的訊息移至資料夾。 按一下 **[確定]**。  
  
    > [!NOTE]
    >  如果此資料夾不存在，您可以建立使用**建立新資料夾**命令。  
  
12. 在 [FILE 傳輸屬性] 對話方塊中**檔案遮罩**方塊中，輸入  **\*。\<*延伸*>**，其中\<*延伸*> 是個內送的延伸模組一般檔案訊息，例如**.txt**。 按一下 **[確定]**。  
  
13. 在 [接收位置屬性] 對話方塊中，確定**BizTalkServerApplication**輸入**接收處理常式**方塊。  
  
14. 如**接收管線**方塊中，從下拉式清單中選取自訂接收管線。  
  
15. 按一下**套用**，然後按一下 **確定**。  
  
16. 在 BizTalk Server 管理主控台中，按一下 **接收位置**，以滑鼠右鍵按一下您剛才的接收位置建立，，然後按一下**啟用**。  
  
    > [!NOTE]
    >  啟用接收位置之後，BizTalk 會主動輪詢檔案資料夾。
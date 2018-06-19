---
title: 建立 A4SWIFT 傳送埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, send ports
- send ports, creating
ms.assetid: d1ee18f8-a6aa-4cd5-9e65-fb2e0fa2d0c2
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1cf24cb99643acc869123450ce14fd5050ee7408
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22210246"
---
# <a name="creating-an-a4swift-send-port"></a>建立 A4SWIFT 傳送埠
您必須建立傳送埠以啟用[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]SWIFT 網路時，傳送訊息，如下圖所示。 此傳送埠會傳送至輸出檔案資料夾的一般檔案訊息。 此傳送埠被為了與 Message Repair 和 New Submission 功能運作。  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-send-port-configuration.gif "A4SWIFT_Send_Port_Configuration")  
  
 **摘要**  
  
 建立並啟動具有下列屬性和元件的靜態單向傳送埠：  
  
|屬性/元件|設定|  
|-------------------------|-------------|  
|傳送埠|靜態單向連接埠|  
|傳輸類型|FILE|  
|目的資料夾 (位址 URI)|您想要從傳送訊息的資料夾名稱|  
|檔案名稱 （位址的 URI）|%MessageID%.txt|  
|篩選|下表中所述|  
  
### <a name="to-add-the-sent-port"></a>新增傳送的埠  
  
1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
2.  在 [傳送埠屬性] 對話方塊中**名稱**方塊中，輸入傳送埠的名稱。  
  
3.  在**傳輸** 區段中，針對**類型**方塊中，按一下下拉式清單，並選取**檔案**。  
  
4.  按一下**設定**按鈕右邊的 [類型] 下拉式清單。  
  
5.  在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。  
  
6.  在 [瀏覽資料夾] 對話方塊中，移至您想要從傳送訊息的資料夾。 按一下 **[確定]**。  
  
    > [!NOTE]
    >  如果此資料夾不存在，您可以建立使用**建立新資料夾**命令。  
  
7.  在**檔案名稱**方塊中，輸入 **%MessageID%.txt**，然後按一下 **確定**。  
  
8.  在**傳送埠屬性**對話方塊方塊中，按一下下拉式清單，如**傳送管線**] 方塊中，然後選取 [自訂傳送管線。  
  
9. 在左窗格中，按一下 **篩選**，然後執行下列步驟：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性**|選取**BTS。作業**。|  
    |**運算子**|選取 **==** 。|  
    |**值**|型別**A4SWIFT_MRSRCompleted**。|  
    |**群組**|選取**或者。**|  
    |**屬性**|選取**BTS。作業**。|  
    |**運算子**|選取 **==** 。|  
    |**值**|型別**A4SWIFT_MRSRFailed**。|  
    |**群組**|選取**或**。|  
    |**屬性**|選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**。|  
    |**運算子**|選取 **==** 。|  
    |**值**|型別**True**。|  
  
10. 按一下**套用**，然後按一下  **確定。**  
  
11. 在**傳送埠** 窗格中，以滑鼠右鍵按一下傳送埠，然後**啟動**。
---
title: "如何將選取的對應項目在檢視 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e287b22-5738-428a-aa35-cced877e51ea
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1dff8e981b65b6b91c744ce26648a5f4e06adea
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-bring-selected-map-items-in-view"></a>如何在檢視中顯示選取的對應項目
使用舊版的 BizTalk 對應工具時，如果對應包含大型的結構描述，您必須手動捲動來源結構描述窗格、格線頁和目標結構描述窗格，才能在單一檢視中包含所有相關的對應項目。 BizTalk Server 與 BizTalk 對應工具可讓您選取的運算質/連結的所有相關對應項目帶入自動捲動格線頁的單一檢視。 本主題提供如何執行此作業的相關資訊。  
  
 依據您的選項 (來源結構描述節點、關係檢視中的元素或目標結構描述節點) 而定，BizTalk 對應工具會以同步方式自動捲動結構描述檢視與關係檢視，並顯示所選項目的整體關係檢視。  
  
> [!NOTE]
>  自動捲動功能要在 BizTalk 對應工具反白所有相關的對應項目後才會生效。 換句話說，首先要反白與選項相關的元素，BizTalk 對應工具才會自動捲動以將相關的元素包含在檢視中。  
  
 BizTalk 對應工具實際上不會移動格線物件。 當您移除或修改選項時，格線物件會回到它們各自的位置。  
  
## <a name="prerequisites"></a>必要條件  
 此作業需要執行中的 BizTalk 對應工具。  
  
### <a name="to-bring-the-selected-map-items-in-view"></a>將所選對應項目包含在檢視中  
  
1.  在對應工具公用程式功能區中，按一下自動捲動圖示![自動 &#45; 捲動圖示](../core/media/mapper-intelliscroll.gif "Mapper_IntelliScroll")以將它關閉。  
  
    > [!NOTE]
    >  ![自動 &#45; 捲動圖示](../core/media/mapper-intelliscroll.gif "Mapper_IntelliScroll")切換圖示依預設關閉。  
  
2.  按一下運算質或連結，就會反白關係中的相關對應項目。  
  
     下圖以藍色顯示選取的連結。 接著，BizTalk 對應工具會強調其他對應項目中的選取範圍，綠色相關。 在下圖中，您可以看到所選關係的所有元素雖已反白，卻未顯示於目前的檢視中。  
  
     ![連結時自動 &#45; 捲動關閉](../core/media/autoscroll-switchoff.gif "AutoScroll_SwitchOff")  
  
3.  按一下自動捲動圖示![自動 &#45; 捲動圖示](../core/media/mapper-intelliscroll.gif "Mapper_IntelliScroll")以將它開啟。  
  
     BizTalk 對應工具會自動捲動，以將選項中所有相關的項目包含在目前的對應檢視中。  
  
     ![開啟自動捲動時檢視](../core/media/autoscroll-switchon.gif "AutoScroll_SwitchOn")  
  
    > [!NOTE]
    >  或者，您也可以按鍵盤的 CTRL+M、CTRL+U。 如需對應工具鍵盤快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。  
  
## <a name="see-also"></a>請參閱  
 [在 BizTalk 對應工具中使用增強功能](../core/using-enhanced-features-in-biztalk-mapper.md)
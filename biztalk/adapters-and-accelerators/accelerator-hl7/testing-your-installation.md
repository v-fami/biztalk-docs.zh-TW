---
title: "測試安裝 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing installation
- installing, testing installation
ms.assetid: db27a75c-db7f-46ff-b8ef-2624ff18dcc8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a813634f2fe03d427ef5d0b14688ecca977f571
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="testing-your-installation"></a>測試您的安裝
您可以設定您[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]進行測試以手動方式執行端對端教學課程，或執行端對端教學課程程式的安裝。 若要執行程式，請按一下**啟動教學課程**按鈕在安裝期間，或是執行 C:\Program Files\Microsoft BizTalk EndToEndTutorial.exe\<版本 > Accelerator for HL7\SDK\End 端對端教學課程（在執行安裝和組態） 之後的資料夾。 這些自動化的動作將會執行相同的設定步驟，您必須手動執行透過本教學課程執行。 端對端教學課程程式會執行下列動作：  
  
-   部署 MSH 和通知結構描述  
  
-   部署版本 2.3.1 通用結構描述  
  
-   部署 ADT 結構描述  
  
-   建立 Tutorial_1WayReceive 接收埠  
  
-   建立 Tutorial_MLLPReceive 接收位置  
  
-   建立 Tutorial_BTAHL7PickUp 接收埠  
  
-   建立 Tutorial_FileReceiveLoc 接收位置  
  
-   建立 Tutorial_sendAck_ADT 傳送埠  
  
-   建立 Tutorial_sendMsg_RX 傳送埠  
  
-   建立 Tutorial_BTAHL7Drop 傳送埠  
  
-   建立 Tutorial_MLLPSend 傳送埠  
  
-   建立 Tutorial_ADTSystem 合作對象  
  
-   建立 Tutorial_RXSystem 合作對象  
  
-   建立 Tutorial_HISystem 合作對象  
  
-   重新啟動 BizTalk 服務  
  
 如果您有執行端對端教學課程程式，您可以省略 for HL7 預先定義的資料夾中的測試執行個體。 該資料夾相關聯的接收管線會拾取訊息，並予以處理。 根據篩選器，傳送管線將傳送至目的地資料夾的文件。 這個簡單的 「 往返 」 會執行基本建置組塊的[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 引擎，並確認您的安裝。  
  
### <a name="to-test-your-installation"></a>若要測試您的安裝  
  
1.  使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至\<*磁碟機*>: \Program Files\Microsoft BizTalk\<版本 > Accelerator for HL7\SDK\End 端對端教學課程的資料夾。  
  
2.  以滑鼠右鍵按一下**TutorialSampleInstance.txt**檔案，然後再按一下**複製**。  
  
3.  使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至\<*磁碟機*>: \Program Files\Microsoft BizTalk\<版本 > Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_BTAHL7PickUp 資料夾。  
  
4.  以滑鼠右鍵按一下資料夾，然後按一下**貼上**。  
  
5.  使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至\<*磁碟機*>: \Program Files\Microsoft BizTalk\<版本 > Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_BTAHL7Drop 資料夾。  
  
     您可以確認您的安裝是否成功，如果已處理的執行個體出現在**Tutorial_BTAHL7Drop**資料夾\< *Guid*>.txt。  
  
 繼續進行下一個步驟中，[準備使用本教學課程](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial2.md)。
---
title: 測試您的安裝 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- testing installation
- installing, testing installation
ms.assetid: db27a75c-db7f-46ff-b8ef-2624ff18dcc8
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d2d94ffce01bd299ad836b7f1fb7c82f66a8196
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971903"
---
# <a name="testing-your-installation"></a>測試您的安裝
您可以設定您[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]進行測試以手動方式執行端對端教學課程，或執行端對端教學課程程式的安裝。 若要執行程式，請按一下**啟動的教學課程**按鈕在安裝期間，或在 C:\Program Files\Microsoft BizTalk 執行 EndToEndTutorial.exe\<版本\>Accelerator for HL7\SDK\端對端教學課程的資料夾 （在之後執行安裝和設定）。 這些自動化動作會執行相同的安裝步驟，您會以手動方式執行來完成教學課程。 端對端教學課程程式會執行下列動作：  
  
- 部署 MSH 和通知結構描述  
  
- 部署第 2.3.1 版通用結構描述  
  
- 部署 ADT 結構描述  
  
- 建立 Tutorial_1WayReceive 接收埠  
  
- 建立 Tutorial_MLLPReceive 接收位置  
  
- 建立 Tutorial_BTAHL7PickUp 接收埠  
  
- 建立 Tutorial_FileReceiveLoc 接收位置  
  
- 建立 Tutorial_sendAck_ADT 傳送埠  
  
- 建立 Tutorial_sendMsg_RX 傳送埠  
  
- 建立 Tutorial_BTAHL7Drop 傳送埠  
  
- 建立 Tutorial_MLLPSend 傳送埠  
  
- 建立 Tutorial_ADTSystem 合作對象  
  
- 建立 Tutorial_RXSystem 合作對象  
  
- 建立 Tutorial_HISystem 合作對象  
  
- 重新啟動 BizTalk 服務  
  
  如果您已執行的端對端教學課程的程式，您可以省略 for HL7 的預先定義的資料夾中的測試執行個體。 與資料夾相關聯的接收管線會拾取訊息，並予以處理。 根據篩選器，傳送管線將傳送至目的地資料夾的文件。 這個簡單的 「 往返 」 練習 Microsoft 的基本建置組塊[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 引擎，並確認您的安裝。  
  
### <a name="to-test-your-installation"></a>若要測試您的安裝  
  
1. 使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端教學課程的資料夾。  
  
2. 以滑鼠右鍵按一下**TutorialSampleInstance.txt**檔案，然後再按一下**複製**。  
  
3. 使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_BTAHL7PickUp 資料夾中。  
  
4. 以滑鼠右鍵按一下資料夾，然後按一下**貼上**。  
  
5. 使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_BTAHL7Drop 資料夾中。  
  
    您可以確認您的安裝是否成功，如果已處理的執行個體出現在**Tutorial_BTAHL7Drop**的資料夾\< *Guid*\>.txt。  
  
   請繼續進行下一個步驟中，[準備使用教學課程](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial2.md)。
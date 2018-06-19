---
title: 準備使用 Tutorial1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4a792b2-8351-4ae8-9d7c-75420c00af03
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efedfeb184b8b0105b8622b6b3f068faffd6a906
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225206"
---
# <a name="preparing-to-use-the-tutorial"></a>準備使用本教學課程
您必須執行下列使用 A4SWIFT 配接器的端對端教學課程之前。  
  
1.  此教學課程中，您將需要下列 SWIFT 成品：  
  
    -   SWIFT 聯盟閘道 (SAG) 6.1  
  
    -   遠端存取 (RA) 6.1  
  
    -   SWIFT WebStation 6.0  
  
    -   SWIFTNet 連結 (SNL) 6.1  
  
2.  您必須設定 SAG: SAG，在建立 MessagePartners、 結束點和路由規則，並測試安裝介面卡的電腦上的 SAG 連線。 如需資訊，請參閱 SAG 文件。  
  
3.  請遵循列於主題 「 如何以建立新主機 」 在 Microsoft BizTalk Server 說明中的指示 ([http://go.microsoft.com/fwlink/?LinkId = 100422](http://go.microsoft.com/fwlink/?LinkId=100422)) 若要建立一個 InterAct 配接器的內含式主控件名稱為*interacthost*，而另一個內含式主控件 FileAct 配接器，名為*fileacthost*。 建立配接器處理常式時，您將使用這些主機。  
  
4.  教學課程中建立下列資料夾：  
  
    -   c:\SWIFTAdapterTutorial\Fileact\ClientLocation  
  
    -   c:\SWIFTAdapterTutorial\Fileact\FileRequestDropRealTime  
  
    -   c:\SWIFTAdapterTutorial\Fileact\ResponseClient  
  
    -   c:\SWIFTAdapterTutorial\Fileact\ResponseServer  
  
    -   c:\SWIFTAdapterTutorial\Fileact\ServerLocation  
  
    -   c:\SWIFTAdapterTutorial\Fileact\StatusEvents  
  
    -   c:\SWIFTAdapterTutorial\Fileact\PullRequest  
  
    -   c:\SWIFTAdapterTutorial\Fileact\PullResponse  
  
    -   c:\SWIFTAdapterTutorial\Interact\HandleRequest  
  
    -   c:\SWIFTAdapterTutorial\Interact\InputRequest_RealTime  
  
    -   c:\SWIFTAdapterTutorial\Interact\InputRequest_SnF  
  
    -   c:\SWIFTAdapterTutorial\Interact\Response  
  
    -   c:\SWIFTAdapterTutorial\Interact\PullRequest  
  
    -   c:\SWIFTAdapterTutorial\Interact\Pullresponse  
  
5.  您必須擁有 SWIFT ITB 的連接或測試配接器的實際環境。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk FileAct 和互動配接器的端對端教學課程](../../adapters-and-accelerators/fileact-interact/biztalk-fileact-and-interact-adapters-end-to-end-tutorial.md)   
 [互動即時案例](../../adapters-and-accelerators/fileact-interact/interact-real-time-scenario.md)   
 [儲存和轉送 (Push) 的案例進行互動](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md)   
 [FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md)   
 [FileAct 存放與轉寄的案例](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md)
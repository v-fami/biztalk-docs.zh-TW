---
title: 步驟 2： 將 SWIFTNet 設定新增至 Paramfile 針對 FileAct 儲存和轉寄案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 088ab41f-8325-4330-b6f2-0164aa1911b1
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a287c6063ff60b08a53ec4f05d45da9225f1c30
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998239"
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-fileact-store-and-forward-scenario"></a>步驟 2： 將 SWIFTNet 設定新增至 Paramfile 針對 FileAct 儲存和轉寄案例
若要啟用這些值初始化的接收者 SWIFTNet paramfile 中必須指定 SAG 中建立的伺服器訊息夥伴。  
  
完整[步驟 1： 設定 SWIFT 配接器針對 FileAct 儲存和轉寄案例](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-store-and-forward-scenario.md)開始此步驟之前。
  
## <a name="add-swiftnet-configuration-to-the-paramfile"></a>將 SWIFTNet 設定新增至 paramfile  
  
1. 在文字編輯器中，例如 [記事本] 開啟 paramfile。  
  
2. Paramfile 通常是位於： C:\SWIFTAlliance\RA\Ra1\cfg\paramfile  
  
3. 在 paramfile，請反白顯示的變更指定伺服器訊息的夥伴名稱：  
    
    username:snlowner  
  
    subsystem_name:FileactStub  
  
    \#subsystem_group:fileactsnf  
  
    \#subsystem_dependency:Support Swarm  
  
    subsystem_nature： 重要  
  
    subsystem_start:  
  
    **繁衍"snlreceiver-SagMessagePartner \<fileact SnF 的伺服器 MessagePartnerName\> -AdapterMode fileact"**  
  
    * 結束  
  
    subsystem_stop:  
  
    * KILL9:snlreceiver  
  
    * 結束  
  
    subsystem_status:  
  
    * NB:1:snlreceiver  
  
    * 結束  
  
    start_event:SNL001:subsystem FileactStubSnF 已啟動  
  
    stop_event:SNL002:subsystem FileactStubSnF 已關閉  
  
    \#subsystem_name:User  
  
    \## subsystem_group:user  
  
    \## subsystem_dependency:  
  
    \#subsystem_nature： 重要  
  
    \#subsystem_start:  
  
    \#* 結束  
  
    \#subsystem_stop:  
  
    \#* 結束  
  
    \#subsystem_status:  
  
    \#* 結束  
  
    # <a name="starteventsnl001subsystem-user-is-up"></a>start_event:SNL001:subsystem 使用者已啟動  
  
    # <a name="stopeventsnl002subsystem-user-is-down"></a>stop_event:SNL002:subsystem 使用者已關閉  
    
  
## <a name="complete-steps"></a>完成步驟
 [FileAct 儲存和轉寄案例](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md)   
 [步驟 1： 設定 SWIFT 配接器針對 FileAct 儲存和轉寄案例](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-store-and-forward-scenario.md)   
 [步驟 3： 建立傳送埠和接收埠針對 FileAct 儲存和轉寄案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md)   
 [步驟 4：測試 FileAct 儲存和轉寄端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md)
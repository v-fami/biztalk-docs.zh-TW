---
title: 步驟 2： 針對 FileAct 即時案例將 SWIFTNet 設定新增至 Paramfile |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4feec3f-4755-477e-b3d6-1dd6d075255e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f40da4b503a5b29e161b376fc25f535c338f5f42
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010559"
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-fileact-real-time-scenario"></a>步驟 2： 針對 FileAct 即時案例將 SWIFTNet 設定新增至 Paramfile
若要啟用這些值初始化的接收者 SWIFTNet paramfile 中必須指定 SAG 中建立的伺服器訊息夥伴。  
  
 在開始此步驟之前，必須先完成[步驟 1： 針對 FileAct 即時案例設定 SWIFT 配接器](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-real-time-scenario.md)。  
  
### <a name="to-add-swiftnet-configuration-to-the-paramfile"></a>若要將 SWIFTNet 設定新增至 paramfile  
  
1. 在文字編輯器中，例如 [記事本] 開啟 paramfile。  
  
   > [!NOTE]
   >  Paramfile 通常是位於： C:\SWIFTAlliance\RA\Ra1\cfg\paramfile  
  
2. 在 paramfile，請反白顯示的變更指定伺服器訊息的夥伴名稱：  
  
    username:snlowner  
  
    subsystem_name:FileactStub  
  
    \#subsystem_group:fileact  
  
    \#subsystem_dependency:Support Swarm  
  
    subsystem_nature： 重要  
  
    subsystem_start:  
  
    **繁衍"snlreceiver-SagMessagePartner \<fileact RT 的伺服器 MessagePartnerName \> -AdapterMode fileact"**  
  
    * 結束  
  
    subsystem_stop:  
  
    * KILL9:snlreceiver  
  
    * 結束  
  
    subsystem_status:  
  
    * NB:1:snlreceiver  
  
    * 結束  
  
    start_event:SNL001:subsystem FileactStub 已啟動  
  
    stop_event:SNL002:subsystem FileactStub 已關閉  
  
    \#subsystem_name:User  
  
    \## subsystem_group:user  
  
    \## subsystem_dependency:  
  
    \#subsystem_nature： 重要  
  
    \#subsystem_start:  
  
    \#* 結束  
  
    \#subsystem_stop:  
  
    \#* 結束  
  
    \#subsystem_status:  
  
    # <a name="end"></a>* 結束  
  
    # <a name="starteventsnl001subsystem-user-is-up"></a>start_event:SNL001:subsystem 使用者已啟動  
  
    # <a name="stopeventsnl002subsystem-user-is-down"></a>stop_event:SNL002:subsystem 使用者已關閉  
  
## <a name="see-also"></a>另請參閱  
 [FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md)   
 [步驟 1： 針對 FileAct 即時案例設定 SWIFT 配接器](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-real-time-scenario.md)   
 [步驟 3： 建立傳送埠和接收埠以進行 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md)   
 [步驟 4：測試 FileAct 即時端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-real-time-end-to-end-scenario.md)
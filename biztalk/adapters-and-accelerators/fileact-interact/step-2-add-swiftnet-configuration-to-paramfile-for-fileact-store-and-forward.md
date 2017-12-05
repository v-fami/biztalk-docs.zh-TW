---
title: "步驟 2： 將 SWIFTNet 組態新增至為 FileAct 存放與轉寄實例 Paramfile |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 088ab41f-8325-4330-b6f2-0164aa1911b1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 394e570ad9bd1c0e7532923dac9c2cc702f2f567
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-fileact-store-and-forward-scenario"></a>步驟 2： 加入為 FileAct 存放與轉寄實例 Paramfile SWIFTNet 組態
若要啟用以這些值來初始化接收者 SWIFTNet paramfile 中必須指定 SAG 中建立的伺服器訊息協力廠商。  
  
完成[步驟 1： 設定 SWIFT 配接器，為 FileAct 存放與轉寄實例](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-store-and-forward-scenario.md)開始此步驟之前。
  
## <a name="add-swiftnet-configuration-to-the-paramfile"></a>將 SWIFTNet 組態新增至 paramfile  
  
1.  在文字編輯器中，例如 [記事本] 開啟 paramfile。  
  
2.  Paramfile 通常是位於： C:\SWIFTAlliance\RA\Ra1\cfg\paramfile  
  
3.  在 paramfile，請指定伺服器訊息夥伴名稱的反白顯示的變更：  
    
     username:snlowner  
  
     subsystem_name:FileactStub  
  
     \#subsystem_group:fileactsnf  
  
     \#subsystem_dependency:Support 群集  
  
     subsystem_nature： 重大  
  
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
  
     \#subsystem_nature： 重大  
  
     \#subsystem_start:  
  
     \#* 結束  
  
     \#subsystem_stop:  
  
     \#* 結束  
  
     \#subsystem_status:  
  
     \#* 結束  
  
     #<a name="starteventsnl001subsystem-user-is-up"></a>start_event:SNL001:subsystem 使用者已啟動  
  
     #<a name="stopeventsnl002subsystem-user-is-down"></a>stop_event:SNL002:subsystem 使用者已關閉  
    
  
## <a name="complete-steps"></a>完成步驟
 [FileAct 存放與轉寄的案例](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md)   
 [步驟 1： 設定為 FileAct 存放與轉寄實例 SWIFT 的配接器](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-store-and-forward-scenario.md)   
 [步驟 3： 建立傳送埠和接收埠為 FileAct 存放與轉寄的實例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md)   
 [步驟 4：測試 FileAct 儲存和轉寄端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md)
---
title: 步驟 2： 將 SWIFTNet 組態新增至 Paramfile 互動存放區和情況 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a18a43c-1dd9-4113-bf32-8bc7bf9338b0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05524abd4cd57b8d804ab5995072905392fd3645
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25963124"
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-interact-store-and-forward-scenario"></a>步驟 2： 將 SWIFTNet 組態新增至 Paramfile 互動存放區和轉寄的案例
若要啟用以這些值來初始化接收者 SWIFTNet paramfile 中必須指定 SAG 中建立的伺服器訊息協力廠商。  
  
 在開始此步驟之前，必須先完成[步驟 1： 設定 SWIFT 配接器，為互動存放與轉寄實例](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md)。  
  
### <a name="to-add-swiftnet-configuration-to-the-paramfile"></a>若要將 SWIFTNet 組態新增至 paramfile  
  
1.  在文字編輯器中，例如 [記事本] 開啟 paramfile。  
  
    > [!NOTE]
    >  Paramfile 通常是位於： C:\SWIFTAlliance\RA\Ra1\cfg\paramfile。  
  
2.  在 paramfile，請指定伺服器訊息夥伴名稱的反白顯示的變更：  
  
     username:snlowner  
  
     subsystem_name:InteractStub  
  
     \#subsystem_group:Interactsnf  
  
     \#subsystem_dependency:Support 群集  
  
     subsystem_nature： 重大  
  
     subsystem_start:  
  
     **繁衍"snlreceiver-SagMessagePartner\<互動 SnF 的伺服器 MessagePartnerName\> -AdapterMode 互動 」**  
  
     * 結束  
  
     subsystem_stop:  
  
     * KILL9:snlreceiver  
  
     * 結束  
  
     subsystem_status:  
  
     * NB:1:snlreceiver  
  
     * 結束  
  
     start_event:SNL001:subsystem InteractStubSnF 已啟動  
  
     stop_event:SNL002:subsystem InteractStubSnF 已關閉  
  
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
  
## <a name="see-also"></a>請參閱  
 [儲存和轉送 (Push) 的案例進行互動](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md)   
 [步驟 1： 設定 SWIFT 配接器互動存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md)   
 [步驟 3： 建立傳送埠和接收埠以進行互動的存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md)   
 [步驟 4：測試 InterAct 儲存和轉寄端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md)
---
title: "最佳化組態 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Max Concurrent Calls parameter
- optimizing, configuration
- configuring, optimizing
- messages, overload protection
ms.assetid: df0ae17b-fcfa-4e00-893c-63f4972d3822
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72b185d7738ac48d9a1dc3631c7c9faec9ac4b60
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-configuration"></a>最佳化組態
本節內容包含如何最佳化 BizTalk Adapter for PeopleSoft Enterprise 組態的相關資訊，並且包含設定配接器時所使用參數的說明。  
  
## <a name="message-overload-protection"></a>訊息多載保護  
 `Max Concurrent Calls` 參數是一項可讓您最佳化組態的功能。 您可以在輸送量超過後端處理能力的情況下使用這個參數。 您可以將參數新增到中的配接器**傳送埠傳輸屬性**對話方塊，即可啟動訊息多載保護。 預設值為 -1，表示呼叫沒有上限。  
  
 當 BizTalk Server 提交訊息給傳輸配接器時，它會先從配接器接收批次，然後在該批次上叫用 `TransmitMessage()` 來傳輸每個訊息。 完成傳輸時，BizTalk Server 會在批次上叫用 `Done()`，這時配接器就會開始將訊息傳輸至後端。 如果 BizTalk Server 在叫用 `Done` 之前會取得多個批次，`Done` 命令可能就永遠不會發生。 藉由設定批次中的訊息數目上限，您便可以控制送到後端的訊息。 此參數的變更會立刻生效。 BizTalk Server 必須擷取 SQL 資料庫中儲存的配接器組態變更。  
  
#### <a name="to-change-the-max-concurrent-calls-parameter"></a>若要變更同時呼叫數目上限參數  
  
1.  在**傳送埠傳輸屬性**對話方塊方塊中，輸入**連接**值。  
  
     預設值為 40 個工作階段。 如果您使用較小的值，則可能會遇到執行階段效能降低的情形。 使用較大的值也是一樣，因為較大的值會超出伺服器的能力，而造成執行階段錯誤。  
  
2.  選取**是**如**重新整理代理程式**強制 runtimeagent.exe 和 browsingagent.exe 程序在必要時自動重新啟動。  
  
     例如，您希望處理程序在與伺服器中斷連線時自動重新啟動，或是您在伺服器加上其他項目，但是該項目並未出現在 Microsoft 配接器精靈的選項中。  
  
     **重新整理代理程式**參數會重新整理瀏覽與執行階段代理程式。 runtimeagent.exe 會在一分鐘之後或是下一次呼叫 Send 時更新。  
  
3.  提供認證以存取 PeopleSoft 系統。  
  
     您可以透過兩種方式來存取系統：  
  
    -   登入認證 (傳輸屬性登入參數)  
  
    -   單一登入 (SSO)  
  
4.  選取**是**如**使用 SSO**使用單一登入。  
  
    > [!NOTE]
    >  如需詳細資訊，請參閱[使用單一登入](../core/using-single-sign-on2.md)。  
  
5.  在清單中選取分支機構應用程式。  
  
     由企業單一登入工具所建立的分支機構應用程式，代表像是 PeopleSoft 的應用程式。 Microsoft BizTalk Adapter for PeopleSoft Enterprise 會使用應用程式使用者的認證。 這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 資料庫中擷取所得。 這些認證就是啟動 BizTalk 專案之使用者 (應用程式使用者) 的認證。  
  
    > [!NOTE]
    >  如需如何建立分支機構應用程式的詳細資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications2.md)，或 Microsoft BizTalk Server 線上說明。  
  
6.  提供所有必要的資訊，以採用連線資訊之後, 按一下**套用**，然後按一下 **確定**。  
  
     您必須設定連線參數，讓 BizTalk Adapter for PeopleSoft Enterprise 能夠存取 PeopleSoft。  
  
## <a name="see-also"></a>另請參閱  
 [建立 PeopleSoft 傳送處理常式](../core/creating-peoplesoft-send-handlers.md)
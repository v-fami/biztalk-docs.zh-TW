---
title: MQSeries 配接器的已知問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c36bcabb-e1eb-455c-8384-00d4682464d3
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be120ec58ebf6ecba62b333655373f3e02f8e487
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990233"
---
# <a name="known-issues-with-the-mqseries-adapter"></a>MQSeries 配接器的已知問題
本節包含可幫助您避免錯誤的資訊。  
  
## <a name="know-issues"></a>已知問題  
  
#### <a name="access-denied-errors-occur-when-attempting-to-send-or-receive-messages"></a>試圖傳送或接收訊息時，發生拒絕存取的錯誤  
  
##### <a name="problem"></a>問題  
 當您使用 MQSeries 配接器傳送訊息到 MQSeries 伺服器或接收來自 MQSeries 伺服器的訊息時，事件檢視器中的應用程式記錄檔會記錄類似下列的錯誤訊息：  
  
```  
The adapter "MQSeries" raised an error message. Details "The adapter has encountered an 'Access Denied' error while attempting to contact the COM+ object on the MQSeries server. Ensure the BizTalk account is added to the Role on the MQSAgent COM+ application."  
```  
  
```  
The adapter failed to transmit message going to send port "MQS://servername/queuename". It will be retransmitted after the retry interval specified for this Send Port. Details: "The adapter has encountered an 'Access Denied' error while attempting to contact the COM+ object on the MQSeries server. Ensure the BizTalk account is added to the Role on the MQSAgent COM+ application."  
```  
  
> [!NOTE]
>  在此錯誤訊息*servername*是伺服器的名稱並*queuename*是佇列的名稱。  
  
 此外，當您嘗試建立設定為使用 BizTalk Adapter for MQSeries 的接收位置或傳送埠時，可能會在事件檢視器中收到下列警告訊息：  
  
```  
The adapter "MQSeries" raised an error message. Details "The adapter has encountered an 'Access Denied' error while attempting to contact the COM+ object on the MQSeries server. Ensure the BizTalk account is added to the Role on the MQSAgent COM+ application."  
```  
  
##### <a name="cause"></a>原因  
 如果下列一或多個狀況成立，可能就會發生這個問題：  
  
- MQSeries 配接器的主控件帳戶沒有 MQSeries 伺服器上 MQSAgent COM+ 應用程式的必要權限。  
  
- 在 [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 或 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 伺服器上，MQSeries 配接器的主控件帳戶不是 MQSeries 伺服器上分散式 COM 使用者群組的成員。  
  
##### <a name="resolution"></a>解決方案  
 若要解決此問題，請使用下列方法。 如果其中一個方法無法解決問題，請嘗試使用下一個方法。  
  
 **方法 1： 上啟用網路 COM + 存取 Microsoft[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)]或[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]-電腦**  
  
 啟用網路 COM + 存取在 Microsoft[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)]或[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]為基礎的電腦，依照所述的步驟[如何啟用網路 COM + 存取 Windows Server 2003 中的](http://go.microsoft.com/fwlink/?LinkId=67076)。  
  
 **方法 2： 設定 MSDTC 設定**  
  
 請依照下列中的步驟**上設定適當的 MSDTC 安全性組態選項[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]** 一節[MSDTC 問題疑難排解](../core/troubleshooting-problems-with-msdtc.md)設定 MSDTC 設定。  
  
 **方法 3： 可讓您確認主控件帳戶已新增至 MQSAgent COM + 應用程式中的角色**  
  
 確認 MQSeries 配接器的主控件帳戶已新增至 MQSeries 伺服器的 MQSAgent COM+ 應用程式中建立的角色。 您可以在「元件服務」管理主控台介面中進行確認。  
  
 **方法 4： 確認 MQSeries 配接器的主控件帳戶是分散式 COM 使用者群組的成員**  
  
 在 Windows 上[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)]或[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]-的伺服器，檢查 MQSeries 配接器的主控件帳戶的群組成員資格。 請確定帳戶的成員**Distributed COM Users**安裝 MQSAgent COM + 應用程式的 MQSeries 伺服器上的群組。  
  
 如需有關 DCOM 安全性增強功能，在 Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，請參閱 < [DCOM 安全性增強功能](http://go.microsoft.com/fwlink/?LinkId=67077)。  
  
## <a name="see-also"></a>另請參閱  
 [MQSeries 配接器疑難排解](../core/troubleshooting-the-mqseries-adapter.md)
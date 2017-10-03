---
title: "設定及檢視稽核記錄檔 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c725bf04-d59f-42c1-b327-b4268421689c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03c88e0a67a393b7ddc35ee8865d99d0299d41f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-and-viewing-audit-logs"></a>設定及檢視稽核記錄檔
ESB 管理入口網站會維護稽核記錄的動作可協助您監視使用量和追蹤問題。 系統管理員可以指定在入口網站會將寫入稽核記錄的事件。  
  
### <a name="to-view-the-audit-logs-for-the-portal"></a>若要檢視稽核記錄檔中的入口網站  
  
1.  指向**Admin**入口網站的主功能表上的索引標籤，然後按一下 [**管理稽核記錄檔**開啟[稽核記錄檔] 頁面](../esb-toolkit/audit-log-page.md)。  
  
2.  若要查看重新提交詳細資料和重新提交訊息的原始訊息，請按一下清單中的訊息，以開啟稽核記錄檔-訊息檢視器 頁面的識別碼。  
  
### <a name="to-configure-the-auditing-settings-for-the-portal"></a>若要設定入口網站的稽核設定  
  
1.  請確定您在入口網站使用 （入口網站管理員的自動成員） 的 BizTalk Server 系統管理員帳戶群組成員的帳戶登入。  
  
2.  指向**Admin**入口網站的主功能表上的索引標籤，然後按一下 [**錯誤設定**開啟入口網站[錯誤設定] 頁面](../esb-toolkit/fault-settings-page.md)。  
  
3.  若要變更的稽核選項，選取核取方塊後**AuditOptions**一節以取得每個您想要稽核的事件。 當重新送出錯誤，可用的事件會儲存已修改的設定，編輯和失敗後成功重新提交的錯誤。
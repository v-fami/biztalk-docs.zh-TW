---
title: 設定及檢視稽核記錄檔 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c725bf04-d59f-42c1-b327-b4268421689c
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03c88e0a67a393b7ddc35ee8865d99d0299d41f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289838"
---
# <a name="configuring-and-viewing-audit-logs"></a><span data-ttu-id="8d1ce-102">設定及檢視稽核記錄檔</span><span class="sxs-lookup"><span data-stu-id="8d1ce-102">Configuring and Viewing Audit Logs</span></span>
<span data-ttu-id="8d1ce-103">ESB 管理入口網站會維護稽核記錄的動作可協助您監視使用量和追蹤問題。</span><span class="sxs-lookup"><span data-stu-id="8d1ce-103">The ESB Management Portal maintains an audit log of actions that help you to monitor usage and track problems.</span></span> <span data-ttu-id="8d1ce-104">系統管理員可以指定在入口網站會將寫入稽核記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="8d1ce-104">Administrators can specify which events the portal will write to the audit log.</span></span>  
  
### <a name="to-view-the-audit-logs-for-the-portal"></a><span data-ttu-id="8d1ce-105">若要檢視稽核記錄檔中的入口網站</span><span class="sxs-lookup"><span data-stu-id="8d1ce-105">To view the audit logs for the portal</span></span>  
  
1.  <span data-ttu-id="8d1ce-106">指向**Admin**入口網站的主功能表上的索引標籤，然後按一下 [**管理稽核記錄檔**開啟[稽核記錄檔] 頁面](../esb-toolkit/audit-log-page.md)。</span><span class="sxs-lookup"><span data-stu-id="8d1ce-106">Point to the **Admin** tab on the portal main menu, and then click **Manage Audit Log** to open the [Audit Log Page](../esb-toolkit/audit-log-page.md).</span></span>  
  
2.  <span data-ttu-id="8d1ce-107">若要查看重新提交詳細資料和重新提交訊息的原始訊息，請按一下清單中的訊息，以開啟稽核記錄檔-訊息檢視器 頁面的識別碼。</span><span class="sxs-lookup"><span data-stu-id="8d1ce-107">To see the resubmission details and the original message for resubmitted messages, click the identifier of a message in the list to open the Audit Log – Message Viewer page.</span></span>  
  
### <a name="to-configure-the-auditing-settings-for-the-portal"></a><span data-ttu-id="8d1ce-108">若要設定入口網站的稽核設定</span><span class="sxs-lookup"><span data-stu-id="8d1ce-108">To configure the auditing settings for the portal</span></span>  
  
1.  <span data-ttu-id="8d1ce-109">請確定您在入口網站使用 （入口網站管理員的自動成員） 的 BizTalk Server 系統管理員帳戶群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="8d1ce-109">Ensure that you log on to the portal using an account that is a member of the BizTalk Server Administrators account group (of which portal administrators are automatically a member).</span></span>  
  
2.  <span data-ttu-id="8d1ce-110">指向**Admin**入口網站的主功能表上的索引標籤，然後按一下 [**錯誤設定**開啟入口網站[錯誤設定] 頁面](../esb-toolkit/fault-settings-page.md)。</span><span class="sxs-lookup"><span data-stu-id="8d1ce-110">Point to the **Admin** tab on the portal main menu, and then click **Fault Settings** to open the portal [Fault Settings Page](../esb-toolkit/fault-settings-page.md).</span></span>  
  
3.  <span data-ttu-id="8d1ce-111">若要變更的稽核選項，選取核取方塊後**AuditOptions**一節以取得每個您想要稽核的事件。</span><span class="sxs-lookup"><span data-stu-id="8d1ce-111">To change the auditing options, select the check boxes in the **AuditOptions** section for each event you want to audit.</span></span> <span data-ttu-id="8d1ce-112">當重新送出錯誤，可用的事件會儲存已修改的設定，編輯和失敗後成功重新提交的錯誤。</span><span class="sxs-lookup"><span data-stu-id="8d1ce-112">The available events are the saving of modified settings, successful resubmission of a fault after editing, and failure when resubmitting a fault.</span></span>
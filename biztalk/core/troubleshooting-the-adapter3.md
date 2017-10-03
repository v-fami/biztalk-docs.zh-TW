---
title: "疑難排解 Adapter3 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters [JD Edwards OneWorld adapters], connecting [Oracle databases]
- JD Edwards OneWorld adapters, troubleshooting
- troubleshooting [JD Edwards OneWorld adapters]
- adapters [JD Edwards OneWorld adapters], troubleshooting
- Oracle databases, connecting [JD Edwards OneWorld adapters]
ms.assetid: 2dd6a951-f113-4f43-b43f-057a239d05c4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15197bcdc84e813d31a8d5292f5559aca1f8ae01
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-the-adapter"></a><span data-ttu-id="baee8-102">配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="baee8-102">Troubleshooting the Adapter</span></span>
<span data-ttu-id="baee8-103">此主題中所含的資訊可幫助您識別和解決在使用 Microsoft BizTalk Adapter for JD Edwards OneWorld 時可能會遇到的問題。</span><span class="sxs-lookup"><span data-stu-id="baee8-103">This topic contains information to help you identify and resolve issues that you might experience while using Microsoft BizTalk Adapter for JD Edwards OneWorld.</span></span>  
  
## <a name="cannot-use-wildcards-in-send-and-receive-port-properties"></a><span data-ttu-id="baee8-104">傳送與接收埠屬性中無法使用萬用字元</span><span class="sxs-lookup"><span data-stu-id="baee8-104">Cannot use wildcards in send and receive port properties</span></span>  
 <span data-ttu-id="baee8-105">Adapter for JD Edwards One World 不支援在下列屬性欄位中使用萬用字元：</span><span class="sxs-lookup"><span data-stu-id="baee8-105">Adapter for JD Edwards One World does not support using wildcards in the following property fields:</span></span>  
  
|<span data-ttu-id="baee8-106">傳送埠屬性</span><span class="sxs-lookup"><span data-stu-id="baee8-106">Send Port Property</span></span>|<span data-ttu-id="baee8-107">接收埠屬性</span><span class="sxs-lookup"><span data-stu-id="baee8-107">Receive Port Property</span></span>|  
|------------------------|---------------------------|  
|<span data-ttu-id="baee8-108">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="baee8-108">Username</span></span>|<span data-ttu-id="baee8-109">事件檔案路徑</span><span class="sxs-lookup"><span data-stu-id="baee8-109">Event File Path</span></span>|  
|<span data-ttu-id="baee8-110">JDE 環境</span><span class="sxs-lookup"><span data-stu-id="baee8-110">JDE Environment</span></span>|<span data-ttu-id="baee8-111">事件目標名稱前置詞</span><span class="sxs-lookup"><span data-stu-id="baee8-111">Event Target Name prefix</span></span>|  
|<span data-ttu-id="baee8-112">Host</span><span class="sxs-lookup"><span data-stu-id="baee8-112">Host</span></span>||  
|<span data-ttu-id="baee8-113">通訊埠</span><span class="sxs-lookup"><span data-stu-id="baee8-113">Port</span></span>||  
|<span data-ttu-id="baee8-114">Java_Home</span><span class="sxs-lookup"><span data-stu-id="baee8-114">Java_Home</span></span>||  
|<span data-ttu-id="baee8-115">JDE JAR 檔案</span><span class="sxs-lookup"><span data-stu-id="baee8-115">JDE JAR Files</span></span>||  
  
## <a name="connecting-to-oracle-database"></a><span data-ttu-id="baee8-116">連線到 Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="baee8-116">Connecting to Oracle database</span></span>  
 <span data-ttu-id="baee8-117">搭配 JD Edwards 使用 Oracle 資料庫時，您必須修改 jdeinterop.ini 檔案。</span><span class="sxs-lookup"><span data-stu-id="baee8-117">When using Oracle database with JD Edwards you must modify the jdeinterop.ini file.</span></span> <span data-ttu-id="baee8-118">使用單一登入，[JDBj-ORACLE] 區段會定義 Oracle tnsnames 位置；必須使用資料庫參數；且 SQLNET.ORA 檔案必須存在 BizTalk Server 電腦上 (這應該會隨附在 Oracle Client 中)。</span><span class="sxs-lookup"><span data-stu-id="baee8-118">Using Single-Sign-On the [JDBj-ORACLE] section defines Oracle tnsnames location; the database parameter must be used; and the SQLNET.ORA file must be present on the BizTalk Server computer (this should be included with the Oracle Client).</span></span>  
  
 <span data-ttu-id="baee8-119">將下列項目加入至 jdeinterop.ini 檔案：</span><span class="sxs-lookup"><span data-stu-id="baee8-119">Add the following to the jdeinterop.ini file:</span></span>  
  
1.  <span data-ttu-id="baee8-120">在 [JDBj-ORACLE] 下，輸入：</span><span class="sxs-lookup"><span data-stu-id="baee8-120">Under [JDBj-ORACLE], type:</span></span>  
  
    ```  
    tns=c:\Oracle\ora92\network\Admin\tnsnames.ora  
    ```  
  
2.  <span data-ttu-id="baee8-121">在 [JDBj-BOOTSTRAP DATA SOURCE] 下，輸入：</span><span class="sxs-lookup"><span data-stu-id="baee8-121">Under [JDBj-BOOTSTRAP DATA SOURCE], type:</span></span>  
  
    ```  
    database=sys810 [hardcode the database name. This information is available in the JDE.ini file on the JD Edwards computer.]  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="baee8-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="baee8-122">See Also</span></span>  
 <span data-ttu-id="baee8-123">[如何建立 JD Edwards OneWorld 傳送埠](../core/how-to-create-send-ports-for-jd-edwards-oneworld.md) </span><span class="sxs-lookup"><span data-stu-id="baee8-123">[How to Create Send Ports for JD Edwards OneWorld](../core/how-to-create-send-ports-for-jd-edwards-oneworld.md) </span></span>  
 [<span data-ttu-id="baee8-124">疑難排解 JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="baee8-124">Troubleshooting JD Edwards OneWorld</span></span>](../core/troubleshooting-jd-edwards-oneworld.md)
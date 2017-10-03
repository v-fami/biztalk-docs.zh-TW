---
title: "疑難排解 Adapter1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards EnterpriseOne adapters, wildcard characters
- adapters [JD Edwards EnterpriseOne adapters], wildcard characters
- wildcard characters, JD Edwards EnterpriseOne adapters
ms.assetid: f5a55e52-039a-4aea-8251-b697fd061ddc
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b77b42854a58d7fe8ffafd177e91f327a7f5e7e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-the-adapter"></a><span data-ttu-id="694d0-102">配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="694d0-102">Troubleshooting the Adapter</span></span>
<span data-ttu-id="694d0-103">本主題所含的資訊，可協助您辨識和解決在使用 Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 時可能會遇到的問題。</span><span class="sxs-lookup"><span data-stu-id="694d0-103">This topic contains information to help you identify and resolve issues that you might experience while using Microsoft BizTalk Adapter for JD Edwards EnterpriseOne.</span></span>  
  
## <a name="cannot-use-wildcards-in-send-port-properties"></a><span data-ttu-id="694d0-104">無法在傳送埠屬性中使用萬用字元</span><span class="sxs-lookup"><span data-stu-id="694d0-104">Cannot use wildcards in send port properties</span></span>  
 <span data-ttu-id="694d0-105">Adapter for JD Edwards Enterprise One 不支援在下列傳送埠屬性欄位中使用萬用字元：</span><span class="sxs-lookup"><span data-stu-id="694d0-105">Adapter for JD Edwards Enterprise One does not support using wildcards in the following send port property fields:</span></span>  
  
-   <span data-ttu-id="694d0-106">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="694d0-106">Username</span></span>  
  
-   <span data-ttu-id="694d0-107">JDE 環境</span><span class="sxs-lookup"><span data-stu-id="694d0-107">JDE Environment</span></span>  
  
-   <span data-ttu-id="694d0-108">Host</span><span class="sxs-lookup"><span data-stu-id="694d0-108">Host</span></span>  
  
-   <span data-ttu-id="694d0-109">通訊埠</span><span class="sxs-lookup"><span data-stu-id="694d0-109">Port</span></span>  
  
-   <span data-ttu-id="694d0-110">Java_Home</span><span class="sxs-lookup"><span data-stu-id="694d0-110">Java_Home</span></span>  
  
-   <span data-ttu-id="694d0-111">JDE JAR 檔案</span><span class="sxs-lookup"><span data-stu-id="694d0-111">JDE JAR Files</span></span>  
  
-   <span data-ttu-id="694d0-112">安全性伺服器名稱</span><span class="sxs-lookup"><span data-stu-id="694d0-112">Security Server Name</span></span>  
  
-   <span data-ttu-id="694d0-113">服務名稱連接</span><span class="sxs-lookup"><span data-stu-id="694d0-113">Service Name Connect</span></span>  
  
-   <span data-ttu-id="694d0-114">資料來源名稱</span><span class="sxs-lookup"><span data-stu-id="694d0-114">Data Source Name</span></span>  
  
-   <span data-ttu-id="694d0-115">資料庫擁有者</span><span class="sxs-lookup"><span data-stu-id="694d0-115">Database Owner</span></span>  
  
-   <span data-ttu-id="694d0-116">資料庫伺服器名稱</span><span class="sxs-lookup"><span data-stu-id="694d0-116">Database Server Name</span></span>  
  
-   <span data-ttu-id="694d0-117">資料庫類型</span><span class="sxs-lookup"><span data-stu-id="694d0-117">Database Type</span></span>  
  
-   <span data-ttu-id="694d0-118">實體資料庫名稱</span><span class="sxs-lookup"><span data-stu-id="694d0-118">Physical Database Name</span></span>  
  
## <a name="connecting-to-oracle-database"></a><span data-ttu-id="694d0-119">連線到 Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="694d0-119">Connecting to Oracle database</span></span>  
 <span data-ttu-id="694d0-120">搭配 JD Edwards 使用 Oracle 資料庫時，您必須修改 jdeinterop.ini 檔案。</span><span class="sxs-lookup"><span data-stu-id="694d0-120">When using Oracle database with JD Edwards you must modify the jdeinterop.ini file.</span></span> <span data-ttu-id="694d0-121">使用單一登入，[JDBj-ORACLE] 區段會定義 Oracle tnsnames 位置；必須使用資料庫參數；且 SQLNET.ORA 檔案必須存在 BizTalk Server 電腦上 (這應該會隨附在 Oracle Client 中)。</span><span class="sxs-lookup"><span data-stu-id="694d0-121">Using Single-Sign-On the [JDBj-ORACLE] section defines Oracle tnsnames location; the database parameter must be used; and the SQLNET.ORA file must be present on the BizTalk Server computer (this should be included with the Oracle Client).</span></span>  
  
 <span data-ttu-id="694d0-122">將下列項目加入至 jdeinterop.ini 檔案：</span><span class="sxs-lookup"><span data-stu-id="694d0-122">Add the following to the jdeinterop.ini file:</span></span>  
  
1.  <span data-ttu-id="694d0-123">在 [JDBj-ORACLE] 下：</span><span class="sxs-lookup"><span data-stu-id="694d0-123">Under [JDBj-ORACLE]:</span></span>  
  
    ```  
    tns=c:\Oracle\ora92\network\Admin\tnsnames.ora  
    ```  
  
2.  <span data-ttu-id="694d0-124">在 [JDBj-BOOTSTRAP DATA SOURCE] 下：</span><span class="sxs-lookup"><span data-stu-id="694d0-124">Under [JDBj-BOOTSTRAP DATA SOURCE]:</span></span>  
  
    ```  
    database=sys810 [hardcode the database name. This information is available in the JDE.ini file on the JD Edwards computer.]  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="694d0-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="694d0-125">See Also</span></span>  
 <span data-ttu-id="694d0-126">[如何建立 JD Edwards EnterpriseOne 的傳送埠](../core/how-to-create-send-ports-for-jd-edwards-enterpriseone.md) </span><span class="sxs-lookup"><span data-stu-id="694d0-126">[How to Create Send Ports for JD Edwards EnterpriseOne](../core/how-to-create-send-ports-for-jd-edwards-enterpriseone.md) </span></span>  
 [<span data-ttu-id="694d0-127">疑難排解 JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="694d0-127">Troubleshooting JD Edwards EnterpriseOne</span></span>](../core/troubleshooting-jd-edwards-enterpriseone.md)
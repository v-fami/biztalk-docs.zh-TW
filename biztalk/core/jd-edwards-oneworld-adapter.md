---
title: JD Edwards OneWorld 配接器 |Microsoft 文件
description: 安裝、 逐步教學課程、 學習架構、 使用 SSO 安全性、 建立您的應用程式、 匯入繫結檔案，以及加入例外狀況處理時使用 BizTalk Adapter for J.D. 在 BizTalk Server Edwards OneWorld
ms.custom: ''
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5df8cd89-d9df-41ca-9a2c-b9d7fbcd06f2
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9bde93503bff679faf2717edefb386aa2f43fc3e
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015927"
---
# <a name="jd-edwards-oneworld-adapter"></a><span data-ttu-id="c5e13-104">JD Edwards OneWorld 配接器</span><span class="sxs-lookup"><span data-stu-id="c5e13-104">JD Edwards OneWorld Adapter</span></span>
<span data-ttu-id="c5e13-105">Microsoft BizTalk Adapter for JD Edwards OneWorld 可讓您在 BizTalk Server 中使用 JD Edwards OneWorld 商務功能。</span><span class="sxs-lookup"><span data-stu-id="c5e13-105">Microsoft BizTalk Adapter for JD Edwards OneWorld enables you to use JD Edwards OneWorld business functions within BizTalk Server.</span></span> <span data-ttu-id="c5e13-106">下列幾節討論設定 BizTalk Adapter for JD Edwards OneWorld 以存取 JD Edwards OneWorld 特定資訊。</span><span class="sxs-lookup"><span data-stu-id="c5e13-106">The following sections discuss setting up BizTalk Adapter for JD Edwards OneWorld to access JD Edwards OneWorld-specific information.</span></span>  
  
## <a name="get-started"></a><span data-ttu-id="c5e13-107">快速入門</span><span class="sxs-lookup"><span data-stu-id="c5e13-107">Get started</span></span> 
<span data-ttu-id="c5e13-108">[開始](../core/getting-started-with-biztalk-adapter-for-jd-edwards-oneworld.md)列出安裝介面卡，並逐步執行教學課程的步驟。</span><span class="sxs-lookup"><span data-stu-id="c5e13-108">[Get started](../core/getting-started-with-biztalk-adapter-for-jd-edwards-oneworld.md) lists the steps to install the adapter, and step through a tutorial.</span></span>

## <a name="architecture"></a><span data-ttu-id="c5e13-109">Architecture</span><span class="sxs-lookup"><span data-stu-id="c5e13-109">Architecture</span></span>
<span data-ttu-id="c5e13-110">[架構](../core/planning-and-architecture17.md)詳細列出配接器的運作方式、 如何執行個體和函式會構成集區在設計階段和執行的階段，限制查詢及擷取清單，當使用多訂單項目，與此配接器。</span><span class="sxs-lookup"><span data-stu-id="c5e13-110">[Architecture](../core/planning-and-architecture17.md) details how the adapter works, how instances and functions are pooled at design time and run time, limitations when  querying and retrieving lists, and using multi-order items with this adapter.</span></span>

## <a name="security"></a><span data-ttu-id="c5e13-111">安全性</span><span class="sxs-lookup"><span data-stu-id="c5e13-111">Security</span></span>
<span data-ttu-id="c5e13-112">[BizTalk Adapter for JD Edwards OneWorld 中的安全性](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)內 BizTalk 伺服器來保護您使用此配接器的應用程式牽涉到使用企業單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="c5e13-112">[Security in BizTalk Adapter for JD Edwards OneWorld](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md) involves using Enterprise Single Sign-on (SSO) within BizTalk Serer to secure your applications that use this adapter.</span></span>

## <a name="create-the-artifacts"></a><span data-ttu-id="c5e13-113">建立的成品</span><span class="sxs-lookup"><span data-stu-id="c5e13-113">Create the artifacts</span></span>
<span data-ttu-id="c5e13-114">[建立應用程式成品](../core/developing-applications3.md)示範如何在 BizTalk 管理中，然後在 Visual Studio 中，將成品新增。</span><span class="sxs-lookup"><span data-stu-id="c5e13-114">[Create the application artifacts](../core/developing-applications3.md) shows you how to add the artifacts in BizTalk Administration, and in Visual Studio.</span></span> <span data-ttu-id="c5e13-115">它也會顯示如何在協調流程中使用訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="c5e13-115">It also shows how to use message context properties in an orchestration.</span></span>

## <a name="import-your-app"></a><span data-ttu-id="c5e13-116">匯入您的應用程式</span><span class="sxs-lookup"><span data-stu-id="c5e13-116">Import your app</span></span>
<span data-ttu-id="c5e13-117">[部署 BizTalk Adapter for JD Edwards OneWorld](../core/deploying-biztalk-adapter-for-jd-edwards-oneworld.md)討論如何將 BizTalk 管理中，匯入您的應用程式的繫結檔案並超過限制。</span><span class="sxs-lookup"><span data-stu-id="c5e13-117">[Deploying BizTalk Adapter for JD Edwards OneWorld](../core/deploying-biztalk-adapter-for-jd-edwards-oneworld.md) discusses how to import your application binding file into BizTalk Administration, and goes over the limitations.</span></span> 

## <a name="exception-handling"></a><span data-ttu-id="c5e13-118">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="c5e13-118">Exception handling</span></span> 
<span data-ttu-id="c5e13-119">[BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling1.md)提供更新 jdearglist.txt 檔案，並將不同的圖形加入至您的協調流程處理的例外狀況的指引。</span><span class="sxs-lookup"><span data-stu-id="c5e13-119">[BizTalk Server exception handling](../core/using-biztalk-server-exception-handling1.md) provides guidance on updating the jdearglist.txt file, and adding different shapes to your orchestration to handle exceptions.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="c5e13-120">疑難排解</span><span class="sxs-lookup"><span data-stu-id="c5e13-120">Troubleshooting</span></span>
<span data-ttu-id="c5e13-121">[疑難排解](../core/troubleshooting-jd-edwards-oneworld.md)描述一些常見的錯誤和情況下，並討論 Windows 事件追蹤。</span><span class="sxs-lookup"><span data-stu-id="c5e13-121">[Troubleshooting](../core/troubleshooting-jd-edwards-oneworld.md) describes some common errors and situations, and discusses Event Tracing for Windows.</span></span>

## <a name="data-types"></a><span data-ttu-id="c5e13-122">資料型別</span><span class="sxs-lookup"><span data-stu-id="c5e13-122">Data Types</span></span>
<span data-ttu-id="c5e13-123">[附錄： 資料型別](../core/appendix-a-data-types.md)列出此配接器所使用的範例資料類型。</span><span class="sxs-lookup"><span data-stu-id="c5e13-123">[Appendix: Data Types](../core/appendix-a-data-types.md) lists the sample data types used by this adapter.</span></span>

## <a name="ui-reference"></a><span data-ttu-id="c5e13-124">UI 參考</span><span class="sxs-lookup"><span data-stu-id="c5e13-124">UI reference</span></span>
<span data-ttu-id="c5e13-125">[BizTalk Adapter for JDE OneWorld 的 UI 參考](../core/ui-reference-for-biztalk-adapter-for-jde-oneworld.md)對話方塊和精靈使用此配接器所提供的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c5e13-125">[UI Reference for BizTalk Adapter for JDE OneWorld](../core/ui-reference-for-biztalk-adapter-for-jde-oneworld.md) provides details on the dialog boxes and wizards used by this adapter.</span></span> 
---
title: JD Edwards EnterpriseOne 配接器 |Microsoft 文件
description: 安裝、 逐步教學課程、 學習架構、 使用 SSO 安全性、 建立您的應用程式、 匯入繫結檔案，以及加入例外狀況處理時使用 BizTalk Adapter for J.D. Edwards EnterpriseOne，BizTalk Server 中
ms.custom: ''
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 97f0f87a-59c3-4503-8da6-d6967dab820a
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e1d82cafd20e8c86fbbf7daa42304ecb95c9aee
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015903"
---
# <a name="jd-edwards-enterpriseone-adapter"></a><span data-ttu-id="aad94-104">JD Edwards EnterpriseOne 配接器</span><span class="sxs-lookup"><span data-stu-id="aad94-104">JD Edwards EnterpriseOne Adapter</span></span>
<span data-ttu-id="aad94-105">Microsoft BizTalk Adapter for J.D.</span><span class="sxs-lookup"><span data-stu-id="aad94-105">Microsoft BizTalk Adapter for J.D.</span></span> <span data-ttu-id="aad94-106">Edwards EnterpriseOne 可讓您使用 BizTalk Server 中的 JD Edwards EnterpriseOne 商務功能。</span><span class="sxs-lookup"><span data-stu-id="aad94-106">Edwards EnterpriseOne enables you to use JD Edwards EnterpriseOne business functions within BizTalk Server.</span></span> <span data-ttu-id="aad94-107">下列各節將討論如何設定配接器以存取 JD Edwards EnterpriseOne 特有資訊。</span><span class="sxs-lookup"><span data-stu-id="aad94-107">The following sections discuss setting up the adapter to access JD Edwards EnterpriseOne-specific information.</span></span>  
  
## <a name="get-started"></a><span data-ttu-id="aad94-108">快速入門</span><span class="sxs-lookup"><span data-stu-id="aad94-108">Get started</span></span>
<span data-ttu-id="aad94-109">[開始](../core/getting-started-with-biztalk-adapter-for-jd-edwards-enterpriseone.md)列出安裝介面卡，並逐步執行某些教學課程的步驟。</span><span class="sxs-lookup"><span data-stu-id="aad94-109">[Get started](../core/getting-started-with-biztalk-adapter-for-jd-edwards-enterpriseone.md) lists the steps to install the adapter, and step through some tutorials.</span></span>

## <a name="architecture"></a><span data-ttu-id="aad94-110">Architecture</span><span class="sxs-lookup"><span data-stu-id="aad94-110">Architecture</span></span>
<span data-ttu-id="aad94-111">[架構](../core/architecture-of-biztalk-adapter-for-jd-edwards-enterpriseone.md)說明的設計階段和執行階段的配接器的元素。</span><span class="sxs-lookup"><span data-stu-id="aad94-111">[Architecture](../core/architecture-of-biztalk-adapter-for-jd-edwards-enterpriseone.md) describes the design time and run time elements of the adapter.</span></span>

## <a name="security"></a><span data-ttu-id="aad94-112">安全性</span><span class="sxs-lookup"><span data-stu-id="aad94-112">Security</span></span>
<span data-ttu-id="aad94-113">[安全性](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md)內 BizTalk 伺服器來保護您使用此配接器的應用程式牽涉到使用企業單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="aad94-113">[Security](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md) involves using Enterprise Single Sign-on (SSO) within BizTalk Serer to secure your applications that use this adapter.</span></span>

## <a name="create-the-artifacts"></a><span data-ttu-id="aad94-114">建立的成品</span><span class="sxs-lookup"><span data-stu-id="aad94-114">Create the artifacts</span></span>
<span data-ttu-id="aad94-115">[建立應用程式成品](../core/developing-applications2.md)示範如何在 BizTalk 管理中，然後在 Visual Studio 中，將成品新增。</span><span class="sxs-lookup"><span data-stu-id="aad94-115">[Create the application artifacts](../core/developing-applications2.md) shows you how to add the artifacts in BizTalk Administration, and in Visual Studio.</span></span> <span data-ttu-id="aad94-116">它也會顯示如何在協調流程中使用訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="aad94-116">It also shows how to use message context properties in an orchestration.</span></span>

## <a name="import-your-app"></a><span data-ttu-id="aad94-117">匯入您的應用程式</span><span class="sxs-lookup"><span data-stu-id="aad94-117">Import your app</span></span>
<span data-ttu-id="aad94-118">[部署應用程式](../core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone.md)討論如何在您的應用程式繫結檔案匯入至 BizTalk 管理中，且會透過任何限制。</span><span class="sxs-lookup"><span data-stu-id="aad94-118">[Deploying your application](../core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone.md) discusses how to import your application binding file into BizTalk Administration, and goes over any limitations.</span></span> 

## <a name="exception-handling"></a><span data-ttu-id="aad94-119">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="aad94-119">Exception handling</span></span>
<span data-ttu-id="aad94-120">[BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling3.md)提供不同的圖形加入您的協調流程處理的例外狀況的指引。</span><span class="sxs-lookup"><span data-stu-id="aad94-120">[BizTalk Server Exception Handling](../core/using-biztalk-server-exception-handling3.md) provides guidance on adding different shapes to your orchestration to handle exceptions.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="aad94-121">疑難排解</span><span class="sxs-lookup"><span data-stu-id="aad94-121">Troubleshooting</span></span>
<span data-ttu-id="aad94-122">[配接器進行疑難排解](../core/troubleshooting-jd-edwards-enterpriseone.md)描述一些常見的錯誤和情況下，並討論 Windows 事件追蹤。</span><span class="sxs-lookup"><span data-stu-id="aad94-122">[Troubleshoot the adapter](../core/troubleshooting-jd-edwards-enterpriseone.md) describes some common errors and situations, and discusses Event Tracing for Windows.</span></span>

## <a name="reference"></a><span data-ttu-id="aad94-123">參考</span><span class="sxs-lookup"><span data-stu-id="aad94-123">Reference</span></span>
<span data-ttu-id="aad94-124">[技術參考](../core/technical-reference6.md)包含範例檔案，以及此配接器所使用的範例資料類型。</span><span class="sxs-lookup"><span data-stu-id="aad94-124">[Technical reference](../core/technical-reference6.md) includes sample files and sample data types used by this adapter.</span></span>

## <a name="ui-reference"></a><span data-ttu-id="aad94-125">UI 參考</span><span class="sxs-lookup"><span data-stu-id="aad94-125">UI reference</span></span>
<span data-ttu-id="aad94-126">[UI 參考](../core/ui-reference-for-biztalk-adapter-for-jd-edwards-enterpriseone.md)對話方塊和精靈使用此配接器所提供的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="aad94-126">[UI reference](../core/ui-reference-for-biztalk-adapter-for-jd-edwards-enterpriseone.md) provides details on the dialog boxes and wizards used by this adapter.</span></span> 
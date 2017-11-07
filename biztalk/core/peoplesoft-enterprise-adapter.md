---
title: "PeopleSoft Enterprise 配接器 |Microsoft 文件"
description: "安裝、 逐步教學課程、 學習架構、 使用 SSO 安全性、 建立您的應用程式、 匯入繫結檔案，以及使用 BizTalk Adapter for PeopleSoft Enterprise 中 BizTalk Server 時加入例外狀況處理"
ms.custom: 
ms.date: 10/19/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c3dd7fd-3566-4063-a2fd-2acbe64d2885
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a3bedda77a7bc45153cda79bd8c011b8628c26b
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="peoplesoft-enterprise-adapter"></a><span data-ttu-id="804fb-103">PeopleSoft Enterprise 配接器</span><span class="sxs-lookup"><span data-stu-id="804fb-103">PeopleSoft Enterprise Adapter</span></span>
<span data-ttu-id="804fb-104">Microsoft BizTalk Adapter for PeopleSoft Enterprise 可讓您使用 BizTalk Server 應用程式中的 PeopleSoft 物件。</span><span class="sxs-lookup"><span data-stu-id="804fb-104">Microsoft BizTalk Adapter for PeopleSoft Enterprise enables you to use PeopleSoft objects within your BizTalk Server application.</span></span> <span data-ttu-id="804fb-105">下列各節討論如何設定配接器存取 PeopleSoft 特定資訊。</span><span class="sxs-lookup"><span data-stu-id="804fb-105">The following sections discuss setting up the adapter to access PeopleSoft-specific information.</span></span>  
  
## <a name="get-started"></a><span data-ttu-id="804fb-106">快速入門</span><span class="sxs-lookup"><span data-stu-id="804fb-106">Get started</span></span>
<span data-ttu-id="804fb-107">[開始](../core/getting-started-with-biztalk-adapter-for-peoplesoft-enterprise.md)列出安裝介面卡，並逐步執行某些教學課程的步驟。</span><span class="sxs-lookup"><span data-stu-id="804fb-107">[Get started](../core/getting-started-with-biztalk-adapter-for-peoplesoft-enterprise.md) lists the steps to install the adapter, and step through some tutorials.</span></span>

## <a name="architecture"></a><span data-ttu-id="804fb-108">Architecture</span><span class="sxs-lookup"><span data-stu-id="804fb-108">Architecture</span></span>
<span data-ttu-id="804fb-109">[架構](../core/architecture-of-biztalk-adapter-for-peoplesoft-enterprise.md)描述與此配接器的驗證與介面方法。</span><span class="sxs-lookup"><span data-stu-id="804fb-109">[Architecture](../core/architecture-of-biztalk-adapter-for-peoplesoft-enterprise.md) describes the interface methods, and validation with this adapter.</span></span>

## <a name="security"></a><span data-ttu-id="804fb-110">安全性</span><span class="sxs-lookup"><span data-stu-id="804fb-110">Security</span></span>
<span data-ttu-id="804fb-111">[安全性](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)內 BizTalk 伺服器來保護您使用此配接器的應用程式牽涉到使用企業單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="804fb-111">[Security](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md) involves using Enterprise Single Sign-on (SSO) within BizTalk Serer to secure your applications that use this adapter.</span></span>

## <a name="create-the-artifacts"></a><span data-ttu-id="804fb-112">建立的成品</span><span class="sxs-lookup"><span data-stu-id="804fb-112">Create the artifacts</span></span>
<span data-ttu-id="804fb-113">[建立應用程式成品](../core/developing-applications4.md)示範如何在 BizTalk 管理中，加入成品，並將結構描述加入至 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="804fb-113">[Create the application artifacts](../core/developing-applications4.md) shows you how to add the artifacts in BizTalk Administration, and add the schemas to Visual Studio.</span></span>

## <a name="import-apps"></a><span data-ttu-id="804fb-114">匯入應用程式</span><span class="sxs-lookup"><span data-stu-id="804fb-114">Import apps</span></span>
<span data-ttu-id="804fb-115">[匯入繫結檔案](../core/deploying-biztalk-adapter-for-peoplesoft-enterprise.md)討論如何在您的應用程式繫結檔案匯入至 BizTalk 管理中，且會透過任何限制。</span><span class="sxs-lookup"><span data-stu-id="804fb-115">[Importing binding file](../core/deploying-biztalk-adapter-for-peoplesoft-enterprise.md) discusses how to import your application binding file into BizTalk Administration, and goes over any limitations.</span></span> 

## <a name="exception-handling"></a><span data-ttu-id="804fb-116">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="804fb-116">Exception handling</span></span>
<span data-ttu-id="804fb-117">[使用例外狀況處理](../core/using-biztalk-server-exception-handling2.md)提供不同的圖形加入您的協調流程處理的例外狀況的指引。</span><span class="sxs-lookup"><span data-stu-id="804fb-117">[Use Exception Handling](../core/using-biztalk-server-exception-handling2.md) provides guidance on adding different shapes to your orchestration to handle exceptions.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="804fb-118">疑難排解</span><span class="sxs-lookup"><span data-stu-id="804fb-118">Troubleshooting</span></span>
<span data-ttu-id="804fb-119">[疑難排解](../core/troubleshooting-peoplesoft.md)描述一些常見的錯誤和情況下，並討論 Windows 事件追蹤。</span><span class="sxs-lookup"><span data-stu-id="804fb-119">[Troubleshooting](../core/troubleshooting-peoplesoft.md) describes some common errors and situations, and discusses Event Tracing for Windows.</span></span>

## <a name="component-interfaces"></a><span data-ttu-id="804fb-120">元件介面</span><span class="sxs-lookup"><span data-stu-id="804fb-120">Component interfaces</span></span>
<span data-ttu-id="804fb-121">[參考](../core/technical-reference-for-peoplesoft-enterprise.md)方法，提供詳細資料，並產生測試您的協調流程的 XML。</span><span class="sxs-lookup"><span data-stu-id="804fb-121">[Reference](../core/technical-reference-for-peoplesoft-enterprise.md) provides details on the methods, and generating XML to test your orchestrations.</span></span>

## <a name="ui-guidance"></a><span data-ttu-id="804fb-122">UI 指導方針</span><span class="sxs-lookup"><span data-stu-id="804fb-122">UI guidance</span></span>
<span data-ttu-id="804fb-123">[UI 參考](../core/ui-reference-for-biztalk-adapter-for-peoplesoft-enterprise.md)對話方塊和精靈使用此配接器所提供的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="804fb-123">[UI Reference](../core/ui-reference-for-biztalk-adapter-for-peoplesoft-enterprise.md) provides details on the dialog boxes and wizards used by this adapter.</span></span> 
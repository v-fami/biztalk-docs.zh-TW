---
title: TIBCO Enterprise Message Service 配接器 |Microsoft 文件
description: 安裝、 逐步教學課程、 學習架構、 使用 SSO 安全性、 建立您的應用程式、 匯入繫結檔案，並使用 BizTalk Adapter for TIBCO EMS，BizTalk Server 中時新增例外狀況處理
ms.custom: ''
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 362556d2-295c-4496-a429-ad7ecc44db76
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 988c7993dd407cb90e267e713a3195f897de9ceb
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24013717"
---
# <a name="tibco-enterprise-message-service-adapter"></a><span data-ttu-id="bb5b3-103">TIBCO Enterprise Message Service 配接器</span><span class="sxs-lookup"><span data-stu-id="bb5b3-103">TIBCO Enterprise Message Service Adapter</span></span>
<span data-ttu-id="bb5b3-104">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service 可讓您發佈和訂閱佇列和主題使用 btsBizTalkServerNoVersion 的 TIBCO EMS 所管理。</span><span class="sxs-lookup"><span data-stu-id="bb5b3-104">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service enables you to publish and subscribe to queues and topics managed by TIBCO EMS using btsBizTalkServerNoVersion.</span></span>  <span data-ttu-id="bb5b3-105">下列各節將討論快速入門中，建立應用程式和多個。</span><span class="sxs-lookup"><span data-stu-id="bb5b3-105">The following sections discuss getting started, creating applications, and more.</span></span>  
   
## <a name="get-started"></a><span data-ttu-id="bb5b3-106">快速入門</span><span class="sxs-lookup"><span data-stu-id="bb5b3-106">Get started</span></span>
<span data-ttu-id="bb5b3-107">[開始](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md)描述配接器功能，安裝配接器，並包含一些教學課程。</span><span class="sxs-lookup"><span data-stu-id="bb5b3-107">[Get started](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md) describes adapter features, installing the adapter, and includes some tutorials.</span></span>

## <a name="architecture"></a><span data-ttu-id="bb5b3-108">Architecture</span><span class="sxs-lookup"><span data-stu-id="bb5b3-108">Architecture</span></span>
<span data-ttu-id="bb5b3-109">[架構](../core/planning-and-architecture16.md)描述配接器如何運作、 提供某些額外的需求，並列出的任何限制。</span><span class="sxs-lookup"><span data-stu-id="bb5b3-109">[Architecture](../core/planning-and-architecture16.md) describes how the adapter works, provides some additional requirements, and lists any limitations.</span></span>

## <a name="security"></a><span data-ttu-id="bb5b3-110">安全性</span><span class="sxs-lookup"><span data-stu-id="bb5b3-110">Security</span></span>
<span data-ttu-id="bb5b3-111">[安全性](../core/security-in-biztalk-adapter-for-tibco-ems.md)內 BizTalk 伺服器來保護您使用此配接器的應用程式牽涉到使用企業單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="bb5b3-111">[Security](../core/security-in-biztalk-adapter-for-tibco-ems.md) involves using Enterprise Single Sign-on (SSO) within BizTalk Serer to secure your applications that use this adapter.</span></span>

## <a name="create-the-artifacts"></a><span data-ttu-id="bb5b3-112">建立的成品</span><span class="sxs-lookup"><span data-stu-id="bb5b3-112">Create the artifacts</span></span>
<span data-ttu-id="bb5b3-113">[建立應用程式成品](../core/developing-applications5.md)列出的步驟來產生結構描述、 建立傳送和接收此配接器，以及如何使用協調流程內的訊息內容屬性所使用的成品。</span><span class="sxs-lookup"><span data-stu-id="bb5b3-113">[Create the application artifacts](../core/developing-applications5.md) lists the steps to generate schemas, create the send and receive artifacts used by this adapter, and how to use the message context properties within an orchestration.</span></span>

## <a name="import-apps"></a><span data-ttu-id="bb5b3-114">匯入應用程式</span><span class="sxs-lookup"><span data-stu-id="bb5b3-114">Import apps</span></span>
<span data-ttu-id="bb5b3-115">[匯入繫結](../core/deploying-biztalk-adapter-for-tibco-enterprise-message-service.md)討論如何在您的應用程式繫結檔案匯入至 BizTalk 管理中，且會透過任何限制。</span><span class="sxs-lookup"><span data-stu-id="bb5b3-115">[Import bindings](../core/deploying-biztalk-adapter-for-tibco-enterprise-message-service.md) discusses how to import your application binding file into BizTalk Administration, and goes over any limitations.</span></span> 

## <a name="handle-exceptions"></a><span data-ttu-id="bb5b3-116">處理例外狀況</span><span class="sxs-lookup"><span data-stu-id="bb5b3-116">Handle exceptions</span></span>
<span data-ttu-id="bb5b3-117">[使用 BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling5.md)提供不同的圖形加入您的協調流程處理的例外狀況的指引。</span><span class="sxs-lookup"><span data-stu-id="bb5b3-117">[Use BizTalk Server Exception Handling](../core/using-biztalk-server-exception-handling5.md) provides guidance on adding different shapes to your orchestration to handle exceptions.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="bb5b3-118">疑難排解</span><span class="sxs-lookup"><span data-stu-id="bb5b3-118">Troubleshooting</span></span>
 <span data-ttu-id="bb5b3-119">[疑難排解](../core/troubleshooting-tibco-enterprise-message-service.md)描述一些常見的錯誤和情況下，並討論 Windows 事件追蹤。</span><span class="sxs-lookup"><span data-stu-id="bb5b3-119">[Troubleshooting](../core/troubleshooting-tibco-enterprise-message-service.md) describes some common errors and situations, and discusses Event Tracing for Windows.</span></span>
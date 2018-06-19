---
title: TIBCO Rendezvous 配接器 |Microsoft 文件
description: 安裝、 逐步教學課程、 學習架構、 使用 SSO 安全性、 建立您的應用程式、 匯入繫結檔案，以及使用 BizTalk Adapter for TIBCO Rendezvous 在 BizTalk Server 時加入例外狀況處理
ms.custom: ''
ms.date: 10/24/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0528954d-11b4-449b-8057-30d463104fef
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b12b4c8382019372efca91b11eda4efa8e3f4b4a
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015453"
---
# <a name="tibco-rendezvous-adapter"></a><span data-ttu-id="cec76-103">TIBCO Rendezvous 配接器</span><span class="sxs-lookup"><span data-stu-id="cec76-103">TIBCO Rendezvous Adapter</span></span>
<span data-ttu-id="cec76-104">Microsoft BizTalk Adapter for TIBCO Rendezvous 可讓您在 BizTalk Server 中使用 TIBCO Rendezvous 商務功能。</span><span class="sxs-lookup"><span data-stu-id="cec76-104">Microsoft BizTalk Adapter for TIBCO Rendezvous enables you to use TIBCO Rendezvous business functions within BizTalk Server.</span></span> <span data-ttu-id="cec76-105">下列各節討論如何設定此配接器以存取 TIBCO Rendezvous 特定資訊。</span><span class="sxs-lookup"><span data-stu-id="cec76-105">The following sections discuss setting up the adapter to access TIBCO Rendezvous-specific information.</span></span>  
  
## <a name="get-started"></a><span data-ttu-id="cec76-106">快速入門</span><span class="sxs-lookup"><span data-stu-id="cec76-106">Get started</span></span>
<span data-ttu-id="cec76-107">[開始](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)描述不同的訊息和概念，並也提供安裝、 結構描述和限制的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="cec76-107">[Get started](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md) describes the different messages and concepts, and also provides details on installation, schemas, and limitations.</span></span> <span data-ttu-id="cec76-108">也請逐步執行某些教學課程，可接收和傳送資料，使用此配接器。</span><span class="sxs-lookup"><span data-stu-id="cec76-108">ALso step through some tutorials to receive and send data using this adapter.</span></span>

## <a name="architecture"></a><span data-ttu-id="cec76-109">Architecture</span><span class="sxs-lookup"><span data-stu-id="cec76-109">Architecture</span></span>
<span data-ttu-id="cec76-110">[架構](../core/architecture-of-biztalk-adapter-for-tibco-rendezvous.md)描述連線能力，以及如何傳遞訊息。</span><span class="sxs-lookup"><span data-stu-id="cec76-110">[Architecture](../core/architecture-of-biztalk-adapter-for-tibco-rendezvous.md) describes the connectivity, and how messages are passed.</span></span>

## <a name="security"></a><span data-ttu-id="cec76-111">安全性</span><span class="sxs-lookup"><span data-stu-id="cec76-111">Security</span></span>
<span data-ttu-id="cec76-112">[安全性](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md)內 BizTalk 伺服器來保護您使用此配接器的應用程式牽涉到使用企業單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="cec76-112">[Security](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md) involves using Enterprise Single Sign-on (SSO) within BizTalk Serer to secure your applications that use this adapter.</span></span>

## <a name="create-applications"></a><span data-ttu-id="cec76-113">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="cec76-113">Create applications</span></span>
<span data-ttu-id="cec76-114">[建立應用程式成品](../core/developing-applications1.md)將示範如何加入接收和傳送成品在 BizTalk 管理、 提供訊息和資料類型對應，以及訊息內容屬性的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="cec76-114">[Create application artifacts](../core/developing-applications1.md) shows you how to add the receive and send artifacts in BizTalk Administration, provides details on message and data type mapping, and message context properties.</span></span>

## <a name="importing-assemblies"></a><span data-ttu-id="cec76-115">匯入的組件</span><span class="sxs-lookup"><span data-stu-id="cec76-115">Importing assemblies</span></span>
<span data-ttu-id="cec76-116">[連接埠和組件匯入](../core/deploying-biztalk-adapter-for-tibco-rendezvous.md)討論如何在您的應用程式繫結檔案匯入至 BizTalk 管理。</span><span class="sxs-lookup"><span data-stu-id="cec76-116">[Import ports and assemblies](../core/deploying-biztalk-adapter-for-tibco-rendezvous.md) discusses how to import your application binding file into BizTalk Administration.</span></span>

## <a name="handle-exceptions"></a><span data-ttu-id="cec76-117">處理例外狀況</span><span class="sxs-lookup"><span data-stu-id="cec76-117">Handle exceptions</span></span>
<span data-ttu-id="cec76-118">[例外狀況處理](../core/using-biztalk-server-exception-handling4.md)提供不同的圖形加入您的協調流程處理的例外狀況的指引。</span><span class="sxs-lookup"><span data-stu-id="cec76-118">[Exception handling](../core/using-biztalk-server-exception-handling4.md) provides guidance on adding different shapes to your orchestration to handle exceptions.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="cec76-119">疑難排解</span><span class="sxs-lookup"><span data-stu-id="cec76-119">Troubleshoot</span></span>
<span data-ttu-id="cec76-120">[對 TIBCO Rendezvous 進行疑難排解](../core/troubleshooting-tibco-rendezvous.md)包含有關使用 Windows 事件追蹤的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="cec76-120">[Troubleshooting TIBCO Rendezvous](../core/troubleshooting-tibco-rendezvous.md) includes details on using Event Tracing for Windows.</span></span>
---
title: Microsoft BizTalk Adapter for mySAP Business Suite 文件 |Microsoft 文件
description: 取得啟動，架構、 安全性、 開發應用程式、 訊息結構描述，以及疑難排解 mySAP 配接器在 BizTalk Adapter Pack
ms.custom: ''
ms.date: 08/16/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26b728d7-f1e9-470a-aba5-10c9f53e2d2b
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb167c3e82eace871301ca4447c6cda39874de5e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217366"
---
# <a name="microsoft-biztalk-adapter-for-mysap-business-suite-documentation"></a><span data-ttu-id="5a20c-103">Microsoft BizTalk Adapter for mySAP Business Suite 文件</span><span class="sxs-lookup"><span data-stu-id="5a20c-103">Microsoft BizTalk Adapter for mySAP Business Suite documentation</span></span>
<span data-ttu-id="5a20c-104">[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]包含許多可協助您了解如何配接器運作方式、 如何建立應用程式，使用配接器，說明不同的連接選項，了解如何建立應用程式和多個資源。</span><span class="sxs-lookup"><span data-stu-id="5a20c-104">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] includes a variety of resources to help you understand how the adapter works, how to create applications that use the adapter, describes the different connection options, learn to create applications, and more.</span></span>

## <a name="get-started"></a><span data-ttu-id="5a20c-105">快速入門</span><span class="sxs-lookup"><span data-stu-id="5a20c-105">Get started</span></span>
<span data-ttu-id="5a20c-106">![開始使用圖示](../../adapters-and-accelerators/adapter-oracle-database/media/f397b0c1-6fe1-4247-a868-9efcab4a5f55.gif "f397b0c1-6fe1-4247-a868-9efcab4a5f55") [開始使用 BizTalk Server](../../core/getting-started-with-biztalk-server.md)包含有關安裝自訂 Rfc 功能、 限制，必要條件，並使用適用於 SAP 的資料提供者相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5a20c-106">![Getting started icon](../../adapters-and-accelerators/adapter-oracle-database/media/f397b0c1-6fe1-4247-a868-9efcab4a5f55.gif "f397b0c1-6fe1-4247-a868-9efcab4a5f55") [Getting started with BizTalk Server](../../core/getting-started-with-biztalk-server.md) includes information on installing the custom RFCs, features, limitations, prerequisites, and info on using the Data Provider for SAP.</span></span>
  
## <a name="tutorials"></a><span data-ttu-id="5a20c-107">教學課程</span><span class="sxs-lookup"><span data-stu-id="5a20c-107">Tutorials</span></span>    

<span data-ttu-id="5a20c-108">![教學課程圖示](../../adapters-and-accelerators/adapter-oracle-database/media/endtoendtutorials.gif "EndtoEndtutorials") [SAP 配接器教學課程](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)涵蓋逐步了解如何使用實驗室[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]針對特定案例。</span><span class="sxs-lookup"><span data-stu-id="5a20c-108">![Tutorials icon](../../adapters-and-accelerators/adapter-oracle-database/media/endtoendtutorials.gif "EndtoEndtutorials") [SAP Adapter Tutorials](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md) covers step-by-step labs to learn how to use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] for specific scenarios.</span></span>

## <a name="architecture"></a><span data-ttu-id="5a20c-109">Architecture</span><span class="sxs-lookup"><span data-stu-id="5a20c-109">Architecture</span></span>  
<span data-ttu-id="5a20c-110">![配接器架構圖示](../../adapters-and-accelerators/adapter-oracle-database/media/4af6a1c5-948f-4bf7-bb56-4d63a47f4825.gif "4af6a1c5-948f-4bf7-bb56-4d63a47f4825") [BizTalk Server 架構](../../core/biztalk-server-architecture.md)概略說明[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，和 WCF。</span><span class="sxs-lookup"><span data-stu-id="5a20c-110">![Adapter Architecture icon](../../adapters-and-accelerators/adapter-oracle-database/media/4af6a1c5-948f-4bf7-bb56-4d63a47f4825.gif "4af6a1c5-948f-4bf7-bb56-4d63a47f4825") [BizTalk Server Architecture](../../core/biztalk-server-architecture.md) provides an overview of the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], and WCF.</span></span>

## <a name="security"></a><span data-ttu-id="5a20c-111">安全性</span><span class="sxs-lookup"><span data-stu-id="5a20c-111">Security</span></span>
<span data-ttu-id="5a20c-112">![社群資源圖示](../../adapters-and-accelerators/adapter-oracle-database/media/community.gif "社群")[保護您的 SAP 應用程式](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md)提供最佳作法和多個安全您使用配接器的訊息。</span><span class="sxs-lookup"><span data-stu-id="5a20c-112">![Community resources icon](../../adapters-and-accelerators/adapter-oracle-database/media/community.gif "Community") [Secure your SAP applications](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md) provides best practices and more for secure your messages using the adapter.</span></span>

## <a name="developing-apps"></a><span data-ttu-id="5a20c-113">開發應用程式</span><span class="sxs-lookup"><span data-stu-id="5a20c-113">Developing apps</span></span>
<span data-ttu-id="5a20c-114">![配接器開發圖示](../../adapters-and-accelerators/adapter-oracle-database/media/44af70c9-cab1-4201-9912-d115cbc7e16f.gif "44af70c9-cab1-4201-9912-d115cbc7e16f") [開發 SAP 應用程式](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)示範如何使用 BizTalk Server 使用配接器[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型時，與 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="5a20c-114">![Adapter Development icon](../../adapters-and-accelerators/adapter-oracle-database/media/44af70c9-cab1-4201-9912-d115cbc7e16f.gif "44af70c9-cab1-4201-9912-d115cbc7e16f") [Develop your SAP applications](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md) shows you how to use the adapters with BizTalk Server, the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model, and the WCF channel model.</span></span>

## <a name="messages-and-message-schemas"></a><span data-ttu-id="5a20c-115">訊息與訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="5a20c-115">Messages and message schemas</span></span>
<span data-ttu-id="5a20c-116">![配接器範例圖示](../../adapters-and-accelerators/adapter-sap/media/2e8eba6a-6ba1-431e-9e0a-f0f45e036e8a.gif "2e8eba6a-6ba1-431e-9e0a-f0f45e036e8a") [訊息與訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)列出的訊息結構和動作記錄的類型，輪詢函式作業和多個。</span><span class="sxs-lookup"><span data-stu-id="5a20c-116">![Adapter Samples icon](../../adapters-and-accelerators/adapter-sap/media/2e8eba6a-6ba1-431e-9e0a-f0f45e036e8a.gif "2e8eba6a-6ba1-431e-9e0a-f0f45e036e8a") [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md) lists the message structure and actions for functions, record types, poling operations, and more.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="5a20c-117">疑難排解</span><span class="sxs-lookup"><span data-stu-id="5a20c-117">Troubleshooting</span></span>
<span data-ttu-id="5a20c-118">![配接器疑難排解圖示](../../adapters-and-accelerators/adapter-oracle-database/media/383a7392-2eb9-485d-b6a8-0187cd5c709d.gif "383a7392-2eb9-485d-b6a8-0187cd5c709d") [SAP 配接器進行疑難排解](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)列出的步驟來啟用追蹤，並列出一些常見的問題和解決方式。</span><span class="sxs-lookup"><span data-stu-id="5a20c-118">![Adapter Troubleshooting icon](../../adapters-and-accelerators/adapter-oracle-database/media/383a7392-2eb9-485d-b6a8-0187cd5c709d.gif "383a7392-2eb9-485d-b6a8-0187cd5c709d") [Troubleshoot the SAP adapter](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md) lists the steps to enable tracing, and lists some common issues and resolutions.</span></span> 



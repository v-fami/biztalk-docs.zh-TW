---
title: "訊息內容屬性來接收 Idoc |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDOCs, message context properties for receiving
ms.assetid: fadb2284-2f55-49c2-bae9-95325f1be539
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca289e37cac15972e75c69d7ad20928b72911963
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-context-properties-for-receiving-idocs"></a><span data-ttu-id="d369e-102">訊息內容屬性，用於接收 Idoc</span><span class="sxs-lookup"><span data-stu-id="d369e-102">Message Context Properties for Receiving IDOCs</span></span>
<span data-ttu-id="d369e-103">接收 IDOC 使用 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]、[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援下列的訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="d369e-103">For receiving an IDOC using Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports the following message context properties.</span></span>  
  
 <span data-ttu-id="d369e-104">**IDOC 控制記錄的屬性。**</span><span class="sxs-lookup"><span data-stu-id="d369e-104">**IDOC Control Record properties.**</span></span>  
  
-   <span data-ttu-id="d369e-105">**TABNAM** -資料表結構的名稱</span><span class="sxs-lookup"><span data-stu-id="d369e-105">**TABNAM** - Name of table structure</span></span>  
  
-   <span data-ttu-id="d369e-106">**MANDT** -用戶端</span><span class="sxs-lookup"><span data-stu-id="d369e-106">**MANDT** - Client</span></span>  
  
-   <span data-ttu-id="d369e-107">**DOCNUM** -IDOC 號碼</span><span class="sxs-lookup"><span data-stu-id="d369e-107">**DOCNUM** - IDOC number</span></span>  
  
-   <span data-ttu-id="d369e-108">**DOCREL** -SAP IDOC 版本</span><span class="sxs-lookup"><span data-stu-id="d369e-108">**DOCREL** - SAP Release for IDOC</span></span>  
  
-   <span data-ttu-id="d369e-109">**狀態**-IDOC 的狀態</span><span class="sxs-lookup"><span data-stu-id="d369e-109">**STATUS** - Status of IDOC</span></span>  
  
-   <span data-ttu-id="d369e-110">**直接**-方向</span><span class="sxs-lookup"><span data-stu-id="d369e-110">**DIRECT** - Direction</span></span>  
  
-   <span data-ttu-id="d369e-111">**OUTMOD** -輸出模式</span><span class="sxs-lookup"><span data-stu-id="d369e-111">**OUTMOD** - Output mode</span></span>  
  
-   <span data-ttu-id="d369e-112">**表現**-覆寫輸入處理中</span><span class="sxs-lookup"><span data-stu-id="d369e-112">**EXPRSS** - Overriding in inbound processing</span></span>  
  
-   <span data-ttu-id="d369e-113">**測試**-測試旗標</span><span class="sxs-lookup"><span data-stu-id="d369e-113">**TEST** - Test flag</span></span>  
  
-   <span data-ttu-id="d369e-114">**IDOCTYP** -基本類型的名稱</span><span class="sxs-lookup"><span data-stu-id="d369e-114">**IDOCTYP** - Name of basic type</span></span>  
  
-   <span data-ttu-id="d369e-115">**CIMTYP** -擴充功能 （客戶定義）</span><span class="sxs-lookup"><span data-stu-id="d369e-115">**CIMTYP** - Extension (defined by customer)</span></span>  
  
-   <span data-ttu-id="d369e-116">**MESTYP** -訊息類型</span><span class="sxs-lookup"><span data-stu-id="d369e-116">**MESTYP** - Message type</span></span>  
  
-   <span data-ttu-id="d369e-117">**MESCOD** -訊息代碼</span><span class="sxs-lookup"><span data-stu-id="d369e-117">**MESCOD** - Message code</span></span>  
  
-   <span data-ttu-id="d369e-118">**MESFCT** -訊息函式</span><span class="sxs-lookup"><span data-stu-id="d369e-118">**MESFCT** - Message function</span></span>  
  
-   <span data-ttu-id="d369e-119">**STD** -EDI 標準，旗標</span><span class="sxs-lookup"><span data-stu-id="d369e-119">**STD** - EDI standard, flag</span></span>  
  
-   <span data-ttu-id="d369e-120">**STDVRS** -EDI 標準、 版本和版次</span><span class="sxs-lookup"><span data-stu-id="d369e-120">**STDVRS** - EDI standard, version and release</span></span>  
  
-   <span data-ttu-id="d369e-121">**STDMES** -EDI 訊息類型</span><span class="sxs-lookup"><span data-stu-id="d369e-121">**STDMES** - EDI message type</span></span>  
  
-   <span data-ttu-id="d369e-122">**SNDPOR** -寄件者的連接埠 （SAP 系統，外部子系統）</span><span class="sxs-lookup"><span data-stu-id="d369e-122">**SNDPOR** - Sender port (SAP System, external subsystem)</span></span>  
  
-   <span data-ttu-id="d369e-123">**SNDPRT** -夥伴寄件者的類型</span><span class="sxs-lookup"><span data-stu-id="d369e-123">**SNDPRT** - Partner type of sender</span></span>  
  
-   <span data-ttu-id="d369e-124">**SNDPFC** -夥伴寄件者的函式</span><span class="sxs-lookup"><span data-stu-id="d369e-124">**SNDPFC** - Partner Function of Sender</span></span>  
  
-   <span data-ttu-id="d369e-125">**SNDPRN** -合作夥伴的寄件者數目</span><span class="sxs-lookup"><span data-stu-id="d369e-125">**SNDPRN** - Partner Number of Sender</span></span>  
  
-   <span data-ttu-id="d369e-126">**SNDSAD** -寄件者地址 (SADR)</span><span class="sxs-lookup"><span data-stu-id="d369e-126">**SNDSAD** - Sender address (SADR)</span></span>  
  
-   <span data-ttu-id="d369e-127">**SNDLAD** -寄件者的邏輯位址</span><span class="sxs-lookup"><span data-stu-id="d369e-127">**SNDLAD** - Logical address of sender</span></span>  
  
-   <span data-ttu-id="d369e-128">**RCVPOR** -接收埠</span><span class="sxs-lookup"><span data-stu-id="d369e-128">**RCVPOR** - Receiver port</span></span>  
  
-   <span data-ttu-id="d369e-129">**RCVPRT** -夥伴類型的接收器</span><span class="sxs-lookup"><span data-stu-id="d369e-129">**RCVPRT** - Partner Type of receiver</span></span>  
  
-   <span data-ttu-id="d369e-130">**RCVPFC** -合作夥伴的收件者的函式</span><span class="sxs-lookup"><span data-stu-id="d369e-130">**RCVPFC** - Partner function of recipient</span></span>  
  
-   <span data-ttu-id="d369e-131">**RCVPRN** -合作夥伴的收件者數目</span><span class="sxs-lookup"><span data-stu-id="d369e-131">**RCVPRN** - Partner number of recipient</span></span>  
  
-   <span data-ttu-id="d369e-132">**RCVSAD**位收件者地址 (SADR)</span><span class="sxs-lookup"><span data-stu-id="d369e-132">**RCVSAD** - Recipient address (SADR)</span></span>  
  
-   <span data-ttu-id="d369e-133">**RCVLAD**位收件者的邏輯位址</span><span class="sxs-lookup"><span data-stu-id="d369e-133">**RCVLAD** - Logical address of recipient</span></span>  
  
-   <span data-ttu-id="d369e-134">**CREDAT** -建立</span><span class="sxs-lookup"><span data-stu-id="d369e-134">**CREDAT** - Created on</span></span>  
  
-   <span data-ttu-id="d369e-135">**CRETIM** -建立時間</span><span class="sxs-lookup"><span data-stu-id="d369e-135">**CRETIM** - Time Created</span></span>  
  
-   <span data-ttu-id="d369e-136">**REFINT** -傳輸檔案 （EDI 交換）</span><span class="sxs-lookup"><span data-stu-id="d369e-136">**REFINT** - Transmission file (EDI Interchange)</span></span>  
  
-   <span data-ttu-id="d369e-137">**REFGRP** -訊息群組 （EDI 訊息群組）</span><span class="sxs-lookup"><span data-stu-id="d369e-137">**REFGRP** - Message group (EDI Message Group)</span></span>  
  
-   <span data-ttu-id="d369e-138">**REFMES** -訊息 （EDI 訊息）</span><span class="sxs-lookup"><span data-stu-id="d369e-138">**REFMES** - Message (EDI Message)</span></span>  
  
-   <span data-ttu-id="d369e-139">**ARCKEY** -訊息外部封存金鑰</span><span class="sxs-lookup"><span data-stu-id="d369e-139">**ARCKEY** - Key for external message archive</span></span>  
  
-   <span data-ttu-id="d369e-140">**序列**-序列化</span><span class="sxs-lookup"><span data-stu-id="d369e-140">**SERIAL** - Serialization</span></span>  
  
-   <span data-ttu-id="d369e-141">**DOCTYP** -IDOC 類型 （這僅提供 EDI_DC。</span><span class="sxs-lookup"><span data-stu-id="d369e-141">**DOCTYP** - IDOC type (This is available in EDI_DC only.</span></span> <span data-ttu-id="d369e-142">應該會出現在內容屬性，但應該只升級為版本 2 Idoc）</span><span class="sxs-lookup"><span data-stu-id="d369e-142">Should be present in the context property but should be promoted for Version 2 IDOCs only)</span></span>  
  
 <span data-ttu-id="d369e-143">**TID** – 代表 SAP 系統所傳送的連入 TRFC 呼叫 TID。</span><span class="sxs-lookup"><span data-stu-id="d369e-143">**TID** – Represents the TID sent by the SAP system for the incoming TRFC call.</span></span>  
  
 <span data-ttu-id="d369e-144">**GUID** – 代表 GUID 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會在內部使用。</span><span class="sxs-lookup"><span data-stu-id="d369e-144">**GUID** – Represents the GUID which the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses internally.</span></span> <span data-ttu-id="d369e-145">這會有一對一的對應，與從 SAP 系統接收 TID。</span><span class="sxs-lookup"><span data-stu-id="d369e-145">This has a one-to-one mapping with the TID which was received from the SAP system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d369e-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d369e-146">See Also</span></span>  
 [<span data-ttu-id="d369e-147">訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="d369e-147">Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)
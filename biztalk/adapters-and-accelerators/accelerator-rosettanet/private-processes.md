---
title: 私用程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- private processes, trading partners
- private processes, about private processes
- private processes, orchestrations
- private processes
- orchestrations, private-process orchestrations
- trading partners, private processes
- BTARN, private processes
- business processes, private processes
ms.assetid: 0c5895eb-22c1-431f-a769-ae6ca05d1e45
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ff99f03b3a38ff9d8c1c33ec16b108e5bd58ca7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967481"
---
# <a name="private-processes"></a>私用程序
Microsoft[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]實作私用程序以將組織內部的商務程序。 公開程序會處理與交易夥伴整合有關的商務程序。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 隔離服務內容處理及後端整合 （在私用程序中） 從 RosettaNet 實作架構 (RNIF) 處理 （在公開程序）。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 私用程序實做為長時間執行的 BizTalk 協調流程。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 您可以使用一個私用程序協調流程上的起始端和回應者端。 每個私用程序都會解譯並處理服務內容訊息部分 (不論是內送或是外寄)。 私用程序會傳送服務內容至公開程序，或是接收來自公開程序的服務內容。 私用程序不會處理標頭，也不會執行 RNIF 處理。 這些工作將留給公開程序來處理。  
  
 在企業實例中，通常每個 PIP 訊息結構描述都會有一個私用程序。 不過，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 包含兩個可以處理任何 PIP 訊息的私用程序協調流程。 一個協調流程做為啟動者程序 (PrivateInitiator.odx，請參閱[PrivateInitiator 範例&#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/privateinitiator-sample.md)) 和另一個做為回應者程序 (PrivateResponder.odx，請參閱[PrivateResponder範例&#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/privateresponder-sample.md))。 您必須自訂私用程序，使 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 適合您特定的商務程序。  
  
 SDK 也包含實作特定 PIP 私用回應者程序以整合商務規則的程序 (PIP3A4PrivateResponder.odx，請參閱[3A4 私用回應者協調流程使用商務規則](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md))。  
  
 私用程序會將服務內容從後端商務營運系統 (LOB) 格式變更為 XML 格式。 變更為 XML 格式之後，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 便會處理服務內容，並且公開程序會將 RNIF 相容標頭新增至服務內容以進行傳輸。  
  
 私用程序會透過 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 資料庫中的 MessageToLOB 及 MessagesFromLOB 資料表，連接至後端商務營運系統應用程式。 這個資料庫負責處理 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 與 LOB 應用程式之間的通訊。 LOB 應用程式會使用介面取得資料庫資料表的存取權。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [啟動者私用程序](../../adapters-and-accelerators/accelerator-rosettanet/initiator-private-process.md)  
  
-   [回應者私用程序](../../adapters-and-accelerators/accelerator-rosettanet/responder-private-process.md)
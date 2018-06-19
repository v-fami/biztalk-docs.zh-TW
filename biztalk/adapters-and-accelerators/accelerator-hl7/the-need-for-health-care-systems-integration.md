---
title: 健康照護系統整合的需求 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- health care organizations
ms.assetid: e747b633-c898-473c-be7d-ba00bfdbdc21
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7674cff1c9c1e787c0ab9638e0abad407adafea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22207230"
---
# <a name="the-need-for-health-care-systems-integration"></a>健康照護系統整合需求
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]醫療保健提供者提供解決方案，其應用程式整合與商務程序自動化所需。 本主題描述一些的商業挑戰該醫療保健組織表面，以及如何加入系統[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]可協助組織符合這些挑戰。 也看看常見實例，示範的範例商務案例[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]。  
  
## <a name="health-care-business-challenge"></a>醫療保健的商業挑戰

醫療保健組織都有許多不同，但相互連線部分的複雜的商務實體。 若是醫院，這些部門可以包含許可、 實驗室、 護士站台、 醫師和計費。 所有這些部門產生及取用資料。 資料可以包含病患、 計費、 程序，以及使用藥物相關資訊。 通常，組織需要這項資料跨許多部門。 醫療保健組織的常見的挑戰是如何有效地處理部門之間的資料交換。  
  
 下圖顯示多少部門可能會與對方進行通訊，建立複雜的系統。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-no-btahl7.gif "hl7_no_btahl7")  
  
 許多這些部門也有不同的商務程序。 部門的人員可以建立、 實作和維護自己的處理序。 這些程序可能會影響其他部門，但人員可能會有的設計不它們記住其他的部門。  
  
 取得處理程序的進一步控制跨組織的完整範圍是許多醫療保健組織的問題。  
  
## <a name="health-care-business-solution"></a>醫療保健商務解決方案

技術可協助解決與商務程序與資料相關的商業難題。 資訊技術 (IT) 系統可協助醫療保健組織轉換從離線、 不相容的處理序，其內部作業成整合、 標準化的程序。  
  
### <a name="integration"></a>整合  
 即使醫療保健組織的不同部分的處理程序不是原本就是相容的您可以將它們整合。 您可以將繫結它們以及點對點連線 （如圖所示健康照護商業挑戰 （在本主題） 為中樞-支點安排方式，如下圖所示系統會將轉換技術。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-yes-btahl7.gif "hl7_yes_btahl7")  
  
[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]連接到每個不同的部門或實體，並提供繫結處理程序在一起的機制，解決其間的差異會進行這項整合。 使商務程序可執行最少的人為介入，它也會自動化資料交換。  
  
### <a name="standardization"></a>標準化  
 一旦您已經連接商務程序，將處理程序可以交換資料。 但是，如果不同部門所維護的資料是以不同格式和系統傳輸它透過不同的資料通訊協定，資料交換可能需要多加用心中系統的設計和自訂。 如果每一個已連線的部門標準化的格式和使用資料交換通訊協定，可以大幅提高效率，此程序。  
  
 這是 HL7 組織已完成。 建立這些醫療保健資料，常見的格式一般檔案結構描述的形式。 工作成果已經很順利完成，到高百分比的大型醫院必須採用其標準的點。  
  
### <a name="solutions-specific-to-the-health-care-industry"></a>醫療保健業界特定方案  
 整合的 IT 系統和標準化的資料交換已提供基礎以更有效率的健全狀況小心處理程序。 醫療保健系統的真正有效 IT 解決方案是著重於該產業中的問題提供的功能、 功能及工具，來解決醫療保健組織的需求。  
  
[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]提供該解決方案。 您安裝[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]最上層的[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]。 [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]使用結構描述所建立和維護 HL7 組織。 此外，它可提供功能與工具，專為醫療保健應用程式。 [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]可啟用批次處理，通知，資料驗證、 稽核和記錄所需醫療保健組織。  
  
## <a name="next"></a>下一個
讀取[範例商務案例](../../adapters-and-accelerators/accelerator-hl7/sample-business-scenario.md)。

---
title: 健康照護系統整合需要 |Microsoft Docs
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
ms.openlocfilehash: b2527b3174b0497025e070a9228f420a31523f24
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972879"
---
# <a name="the-need-for-health-care-systems-integration"></a>健康照護系統整合需求
Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]醫療保健提供者提供解決方案，針對其應用程式整合及商務程序自動化需求。 本主題會描述一些難題，該醫療保健組織的臉，以及如何併入 Microsoft 的系統[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]可協助組織符合這些挑戰。 也看看常見實例，示範的範例商務案例[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]。  
  
## <a name="health-care-business-challenge"></a>醫療保健的商業挑戰

醫療保健的組織都有許多不同，但已連接部分複雜的商務實體。 醫院中，這些部門包括許可、 實驗室、 護理站台、 醫師而言和計費。 所有這些部門產生及取用資料。 資料可以包含病患、 計費、 程序和使用藥物的相關資訊。 通常，組織會需要這項資料跨許多部門。 醫療機構的常見挑戰是如何有效處理部門間的資料交換。  
  
 下圖顯示幾個部門可能會彼此通訊，建立複雜的系統。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-no-btahl7.gif "hl7_no_btahl7")  
  
 許多這些部門也有不同的商務程序。 在部門人員可能會建立、 實作，並維護自己的處理序。 這些程序可能會影響其他部門，但人員可能不具有將它們設計與記住的其他部門。  
  
 取得處理程序的更有效控制跨組織的完整範圍是許多醫療保健組織的問題。  
  
## <a name="health-care-business-solution"></a>醫療保健的商務解決方案

技術可協助解決與商務程序和資料相關的商業難題。 資訊技術 (IT) 系統可協助醫療保健組織轉換成整合、 離線、 不相容的程序，從其內部作業標準化的程序。  
  
### <a name="integration"></a>整合  
 即使醫療機構的不同組件的程序不是原本就是相容的您可以將它們整合。 您可以將其繫結以及點對點連線 （如圖所示健康照護商務挑戰 （在本主題中） 為中樞和支點排列方式，如下圖所示系統會將轉換技術。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-yes-btahl7.gif "hl7_yes_btahl7")  
  
[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] 達成這項整合連線到每個個別的部門或實體，並提供繫結程序在一起的機制，解決其間的差異。 使商務程序可執行最少的人為介入的情況下，它也會自動化資料交換。  
  
### <a name="standardization"></a>標準化  
 一旦您已連接的商務程序，處理程序可以交換資料。 不過，如果不同部門所維護的資料是以不同格式和系統傳輸它透過不同的資料通訊協定，交換資料可能需要更多心力在系統設計和自訂。 如果每個連接部門將標準化的格式和通訊協定搭配其資料交換，即可大幅提高此程序的效率。  
  
 這是 HL7 組織已完成。 建立這些通用的格式，用於醫療保健的資料，一般檔案結構描述的格式。 他們的努力已經很順利完成，到高百分比的大型醫院已採用其標準點。  
  
### <a name="solutions-specific-to-the-health-care-industry"></a>醫療保健產業特有解決方案  
 整合的 IT 系統和標準化的資料交換提供基礎更有效率的健全狀況服務處理程序。 真正發揮功效的 IT 解決方案，適用於醫療保健系統是指將重點放在該產業中，問題，並提供功能、 功能和工具，來解決醫療保健組織的需求。  
  
[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] 提供該解決方案。 在您安裝[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]頂端的[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]。 [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] 使用結構描述建立，並由 HL7 組織所維護。 此外，它提供的功能和工具，專為醫療保健應用程式。 [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] 可啟用批次處理，通知，資料驗證、 稽核和記錄所需的醫療保健組織。  
  
## <a name="next"></a>下一個
讀取[範例商務案例](../../adapters-and-accelerators/accelerator-hl7/sample-business-scenario.md)。

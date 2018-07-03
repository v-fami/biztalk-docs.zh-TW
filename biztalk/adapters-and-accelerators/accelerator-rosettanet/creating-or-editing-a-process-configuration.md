---
title: 建立或編輯程序組態 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- process configuration, modifying
- process configuration, creating
- creating, process configuration
- modifying, process configuration
ms.assetid: 39cc2c93-0986-48d3-8c6f-4280ec9af4e0
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32300e84d2c9102baaa68a57045fefc103d0d9e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013159"
---
# <a name="creating-or-editing-a-process-configuration"></a>建立或編輯程序組態
本節說明如何建立或編輯流程組態，以在 Microsoft 中實作交易夥伴介面程序 (PIP) [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]。 RosettaNet PIP 定義兩個交易夥伴之間的商務程序對話。 在  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]，以建立 PIP 與合作夥伴，您必須先建立程序組態。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 您可以使用此設定檔儲存 PIP 的所有組態特性。 之後，您便可使用此組態，建立交易夥伴的協議。  
  
 如需程序組態屬性，與建立或編輯程序組態的程序的詳細資訊，請參閱[如何建立或編輯流程組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)。  
  
 建立新程序組態時，您的設定必須根據 RosettaNet 組織所維護的 PIP 規格文件。 所有的程序組態設定都來自 PIP 規格，而 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 在大部分設定填入的預設值，都是欄位最常用的值。 您必須確認設定與適當的 PIP 規格中的值一致。 如需有關您所輸入的 PIP 設定如何對應至 PIP 規格中的指導方針的詳細資訊，請參閱 <<c0> [ 使用 PIP 規格建立程序組態](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md)。  
  
 程序組態可以是 RosettaNet 或 CIDX (化學工業資料交換)。 如需有關 CIDX 組態資訊，請參閱[設定 CIDX eStandards 訊息交換](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)。  
  
 當有使用中的程序時，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 不支援變更程序組態。 如果您變更協議，則使用中的程序將會結束，並出現失敗。 所有新的程序將會成功挑選新的組態設定。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何建立或編輯程序設定](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)  
  
-   [使用 PIP 規格建立程序設定](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md)  
  
-   [授權與不可否認性屬性](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md)  
  
-   [設定 CIDX eStandards 訊息交換](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)
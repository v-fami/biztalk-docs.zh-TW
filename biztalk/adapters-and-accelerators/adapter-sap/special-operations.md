---
title: 特殊作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- operations, special operations surfaced by the SAP adapter
ms.assetid: 8725fe63-6ff4-49c8-b386-d4c67e2be440
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bada45064e588748b25947e08b104dc79838ee0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975983"
---
# <a name="special-operations"></a>特殊作業
[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會呈現數個特殊的作業。 這些作業不根據 SAP 系統的成品。 它們會顯示為配接器用戶端應用程式提供功能。 特殊的作業為：  
  
- **RfcGetAttributes**。 此作業的 RFC 節點下的呈現，並公開 （expose） 的 RFC sdk 的功能。 它提供下列 RFC 連線的相關資訊：  
  
  - 系統識別碼  
  
  - 協力廠商程式碼頁面  
  
  - 語言  
  
    如需有關 RfcGetAttributes 作業，包括它的訊息結構描述的詳細資訊，請參閱[RFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)。  
  
- **RfcConfirmTransID**。 這項作業的 TRFC 節點下的呈現，並公開 RFC SDK 功能。 您可以使用這項作業來確認 SAP 系統上的 SAP 交易識別碼。  
  
   如需有關如何使用 RfcConfirmTransID 作業和其訊息結構描述，請參閱[對 sap 的 Trfc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)。  
  
- **字串 SapAdapterUtilities.ConvertGuidToTid(Guid)**。 這是 SAP 配接器組件所公開的公用方法。 （不是由配接器顯示的作業。）它會傳回 SAP 交易識別碼 (TID) 對應至指定的 GUID。  
  
   就內部而言，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]對應至 GUID 的 SAP 系統上的 SAP 交易識別碼 (TID) 識別的工作 (LUW) 邏輯單元。 此 GUID 會公開給配接器用戶端，以便它們可以認可 tRFC (LUW) 叫用 RfcConfirmTransID 作業，以確認其上的 SAP 系統的 TID。  
  
   不過，某些情況下，您可能需要與 tRFC 相關聯的 TID。 例如，您可能想要識別 LUW 上 SAP 系統來疑難排解問題。 針對這些案例，您可以呼叫**ConvertGuidToTid**。 若要使用**ConvertGuidToTid**在您的程式碼中，您必須加入 SAP 配接器組件的參考至您的專案。  
  
   如需有關如何叫用 Trfc 的詳細資訊，請參閱[對 sap 的 Trfc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)。 下列範例示範如何叫用**ConvertGuidToTid**。  
  
  ```  
  // messageGuid is the GUID associated with a tRFC or IDOC  
  
  string tid = SapAdapterUtilities.ConvertGuidToTid(messageGuid);  
  ```  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)
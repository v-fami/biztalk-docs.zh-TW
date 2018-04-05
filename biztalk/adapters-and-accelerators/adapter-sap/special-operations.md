---
title: 特殊作業 |Microsoft 文件
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
ms.openlocfilehash: fe2472d905e9e726b827d44da79bdfe840233354
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="special-operations"></a>特殊作業
[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現數個特殊的作業。 這些作業不根據 SAP 系統成品。 它們會顯示為配接器用戶端應用程式提供功能。 是特殊作業：  
  
-   **RfcGetAttributes**。 RFC 節點底下會顯示這項作業，並公開 （expose） 的 RFC sdk 的功能。 它提供 RFC 連線的下列資訊：  
  
    -   系統識別碼  
  
    -   夥伴字碼頁  
  
    -   語言  
  
     如需 RfcGetAttributes 作業，包括其訊息結構描述的詳細資訊，請參閱[RFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)。  
  
-   **RfcConfirmTransID**。 這項作業會顯示一個 TRFC 節點下，並公開 RFC SDK 功能。 您可以使用這項作業來確認 SAP 系統上的 SAP 交易識別碼。  
  
     如需有關如何使用 RfcConfirmTransID 作業以及其訊息結構描述，請參閱[tRFCs SAP 中的作業](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)。  
  
-   **字串 SapAdapterUtilities.ConvertGuidToTid(Guid)**。 這是 SAP 配接器組件所公開的公用方法。 （不是由配接器顯示的作業。）它會傳回 SAP 交易識別碼 (TID) 對應到指定的 GUID。  
  
     就內部而言，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]對應 guid SAP 系統上的 SAP 交易識別碼 (TID) 識別的工作 (LUW) 邏輯單元。 此 GUID 是配接器用戶端使用，以便他們可以承諾 tRFC (LUW) 所公開叫用 RfcConfirmTransID 作業，以確認其 TID SAP 系統上。  
  
     不過，某些情況下，您可能需要 TID tRFC 與相關聯。 例如，您可以識別 LUW SAP 系統上的疑難排解問題。 這些案例，您可以呼叫**ConvertGuidToTid**。 若要使用**ConvertGuidToTid**在您的程式碼中，您必須加入 SAP 配接器組件的參考至您的專案。  
  
     如需叫用 tRFCs 的詳細資訊，請參閱[tRFCs SAP 中的作業](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)。 下列範例示範如何叫用**ConvertGuidToTid**。  
  
    ```  
    // messageGuid is the GUID associated with a tRFC or IDOC  
  
    string tid = SapAdapterUtilities.ConvertGuidToTid(messageGuid);  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)
---
title: EDI 處理的協議的角色 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d81b0449-6656-49f7-a781-5fd60031b3d5
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2125ca348cc8f333b1b223404371ae13b113fe1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980431"
---
# <a name="the-role-of-agreements-in-edi-processing"></a>中協議 EDI 處理的角色
組織會使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]來接收 EDI 訊息，並傳送 EDI 訊息，一或多個交易夥伴。 交易夥伴，接著會定義組織內的商務實體的商務設定檔。 如何交換訊息定義的交易一部分的商務設定檔夥伴的兩個商務設定檔之間的合約。 如需詳細資訊，請參閱 <<c0> [ 交易夥伴管理解決方案的建置組塊](../core/building-blocks-of-a-trading-partner-management-solution.md)。  
  
 您在交易夥伴管理 (TPM) 使用者介面中建立交易夥伴協議。 TPM 畫面位於**合作對象**節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
## <a name="configuring-an-agreement-for-edi-processing"></a>設定協議的 EDI 處理  
 將交換 EDI 訊息使用的所有交易夥伴[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]必須同意通訊參數。 這麼做之後, 組織裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]必須建立 TPM （包括為自己的交易夥伴） 中的交易夥伴、 建立商務設定檔和交易夥伴協議之間的商務設定檔。 交易夥伴協議的一部分，您可以設定屬性如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]接收 EDI 訊息，並傳送 EDI 訊息給交易夥伴的商務設定檔。 在其結束時，其他交易夥伴必須執行相同，，交換訊息，組態必須相容。  
  
 您必須定義下列幾組屬性進行 EDI 通訊。  
  
- 交易的交易夥伴屬性會定義一般層面的交易夥伴，例如名稱、 傳送埠以及簽章的憑證。  
  
- 定義商務識別的商務設定檔屬性。  
  
- EDI 屬性，做為交易夥伴協議的一部分，定義如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會處理來自交易夥伴以及如何產生繫結至交易夥伴的外寄訊息的傳入訊息。  
  
- AS2 屬性，做為交易夥伴協議的一部分，定義如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行 AS2 通訊，傳入和傳出。 這些屬性只會在 EDI 訊息是透過 AS2 傳送時，才會影響 EDI 通訊。  
  
  > [!NOTE]
  >  AS2 協議的 EDI 傳訊的 「 協議相同的商務設定檔指定和分開。 兩個協議一起構成合作關係。  
  
  交易夥伴協議屬性會決定下列特定的處理：  
  
- EDI 信封處理和產生  
  
- 通知處理和產生  
  
- 內送和外寄 EDI 訊息的驗證  
  
- 批次產生  
  
- 狀態報告  
  
  商務識別，可以有特定的值，例如**D-U-N-S (Dun & Bradstreet)**。 特定的名稱有特定的辨識符號，例如"01"代表 Duns。 沒有特定的商務身分識別名稱時，"ZZ"會用於 X12 編碼訊息，"ZZZ"會用於 EDIFACT 編碼訊息，指出由個別實體相互定義的名稱。 值和辨識符號，然後識別商務設定檔。 商務識別的名稱是僅供參考之用;它不是由 BizTalk 執行階段進行處理。  
  
## <a name="determining-an-agreement-for-edi-processing"></a>判斷協議的 EDI 處理  
 任何時候[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]接收 EDI 訊息時，它會嘗試判斷訊息解析為交易夥伴協議。 它會嘗試比對訊息的傳送者辨識符號、 寄件者識別碼、 接收者辨識符號和接收者識別項定義為協議的一部分來解決交易夥伴協議。 如需此程序的詳細資訊，請參閱 <<c0> [ 協議解析、 結構描述探索和授權收到 EDI 訊息](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)。  
  
 任何時候[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會產生要傳送，它會嘗試判斷傳送訊息的商務設定檔所關聯的協議的 EDI 訊息。 它會嘗試比對訊息，並且使用下列其中一項 「 合約 」，以解析合約：  
  
- 內容屬性 AgreementPartIdForSend  
  
- AgreementNameForSend、 SenderPartyNameForSend、 和 ReceiverPartyNameForSend 的內容屬性  
  
- 傳送者辨識符號和識別項和接收者辨識符號和識別項  
  
- 傳送埠名稱  
  
  如需此程序的詳細資訊，請參閱 <<c0> [ 協議解析和外寄 EDI 訊息的結構描述判斷](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md)。  
  
## <a name="using-edi-global-properties"></a>使用 EDI 全域屬性  
 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]無法判斷協議的任一個內送或外寄訊息，它會使用後援協議來處理內送交換或產生外寄交換。 以滑鼠右鍵按一下設定後援協議**合作對象**中的節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，然後按一下**X12 後援設定**（適用於 X12 編碼訊息） 或**EDIFACT 後援設定**（EDIFACT 編碼訊息）。 如需有關全域屬性的詳細資訊，請參閱[設定全域或後援協議屬性](../core/configuring-global-or-fallback-agreement-properties.md)。  
  
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 只有當它無法判斷交換的協議時，就會使用後援協議。 如果已判斷出協議，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]尚未定義的兩個交易夥伴之間的協議屬性不會使用後援協議的屬性值。  
  
 如果連接埠設定需要驗證，就不會使用後援協議。 如果接收埠的通訊埠設定需要驗證 (如果有任一**驗證失敗時捨棄訊息**或是**驗證失敗時保留訊息**上選取**一般**頁面的**接收埠屬性**對話方塊)，都需要接收埠收到的任何交換的協議。 在此情況下，不會使用後援協議。 如果判斷出交換的協議，交換會被視為驗證失敗，並將被擱置。  
  
## <a name="see-also"></a>另請參閱  
 [協議解析、 結構描述探索和授權接收之 EDI 訊息](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)   
 [協議解析和外寄 EDI 訊息的結構描述判斷](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md)   
 [設定 EDI 屬性](../core/configuring-edi-properties.md)   
 [設定全域或後援協議屬性](../core/configuring-global-or-fallback-agreement-properties.md)   
 [EDI 合作對象的已知問題](../core/known-issues-with-edi-parties.md)
---
title: EDI 處理的協議的角色 |Microsoft 文件
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
ms.openlocfilehash: 9986f22108382f1b1128079b8ff8c31902ca2979
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279934"
---
# <a name="the-role-of-agreements-in-edi-processing"></a>中協議 EDI 處理的角色
組織會使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]來接收 EDI 訊息，並傳送 EDI 訊息，一個或多個交易夥伴。 交易夥伴，接著定義組織內的商務實體的商務設定檔。 如何商務設定檔交換訊息定義為屬於交易夥伴的兩個商務設定檔之間的合約。 如需詳細資訊，請參閱[交易夥伴管理解決方案的建置組塊](../core/building-blocks-of-a-trading-partner-management-solution.md)。  
  
 您在交易夥伴管理 (TPM) 使用者介面中建立交易夥伴協議。 TPM 畫面位於**合作對象**節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
## <a name="configuring-an-agreement-for-edi-processing"></a>設定協議的 EDI 處理  
 會交換使用的 EDI 訊息的所有交易夥伴[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]必須同意通訊參數。 這麼做之後, 組織裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]必須建立 TPM （包括其本身的交易夥伴） 中的交易夥伴、 建立商務設定檔，以及交易夥伴協議之間的商務設定檔。 交易夥伴協議的一部分，您可以設定如何屬性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]接收 EDI 訊息，並傳送 EDI 訊息給交易夥伴的商務設定檔。 其終止時，其他交易夥伴必須這麼做，並交換訊息，設定必須相容。  
  
 您必須定義下列幾組屬性進行 EDI 通訊。  
  
-   交易夥伴定義的內容一般層面的交易夥伴，例如名稱、 傳送埠以及簽章憑證。  
  
-   定義商務識別的商務設定檔屬性。  
  
-   EDI 屬性，做為交易夥伴協議的一部分，定義如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會處理內送訊息從交易夥伴以及如何產生外寄訊息繫結至交易夥伴。  
  
-   AS2 屬性，做為交易夥伴協議的一部分，定義如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行 AS2 通訊，傳入和傳出。 這些屬性只會在 EDI 訊息是透過 AS2 傳送時，才會影響 EDI 通訊。  
  
    > [!NOTE]
    >  AS2 協議的 EDI 訊息的 「 協議相同的商務設定檔指定和分開。 兩個協議結合在一起構成合作關係。  
  
 交易夥伴協議屬性會決定下列特定的處理：  
  
-   EDI 信封處理和產生  
  
-   通知處理和產生  
  
-   內送和外寄 EDI 訊息的驗證  
  
-   批次產生  
  
-   狀態報告  
  
 商務識別可以有特定值，例如**D-U-N-S (Dun & Bradstreet)**。 特定名稱具有特定的辨識符號，例如"01"代表 Duns。 沒有特定的商務識別名稱時，X12 編碼訊息會使用"ZZ"，"ZZZ"會用於 EDIFACT 編碼訊息，指出由個別實體相互定義的名稱。 值和辨識符號，然後識別商務設定檔。 商務識別的名稱是僅供參考之用;它不是由 BizTalk 執行階段進行處理。  
  
## <a name="determining-an-agreement-for-edi-processing"></a>判斷協議的 EDI 處理  
 任何時候[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]接收 EDI 訊息時，它會嘗試判斷訊息解析為交易夥伴協議。 它會嘗試比對的訊息傳送者辨識符號、 寄件者識別碼、 接收者辨識符號和接收者識別碼定義為協議的一部分來解決交易夥伴協議。 如需這個程序的詳細資訊，請參閱[協議解析、 結構描述探索和授權接收 EDI 訊息](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)。  
  
 任何時候[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會產生 EDI 訊息傳送，它會嘗試判斷傳送訊息的商務設定檔所關聯的協議。 它會嘗試藉由比對訊息與下列其中一項使用的協議解析協議：  
  
-   內容屬性： AgreementPartIdForSend  
  
-   AgreementNameForSend、 SenderPartyNameForSend、 和 ReceiverPartyNameForSend 內容屬性  
  
-   傳送者辨識符號和識別項以及接收者辨識符號和識別碼  
  
-   傳送埠名稱  
  
 如需這個程序的詳細資訊，請參閱[協議解析和外寄 EDI 訊息的結構描述判斷](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md)。  
  
## <a name="using-edi-global-properties"></a>使用 EDI 全域屬性  
 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]無法判斷協議的其中一個內送或外寄訊息，它會使用後援協議來處理內送交換或產生外寄交換。 設定後援協議以滑鼠右鍵按一下**合作對象**中的節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，然後按一下**X12 後援設定**（針對 X12 編碼訊息） 或**EDIFACT 後援設定**（EDIFACT 編碼訊息）。 如需全域屬性的詳細資訊，請參閱[設定全域或後援協議屬性](../core/configuring-global-or-fallback-agreement-properties.md)。  
  
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]它無法判斷交換的協議時，才會使用後援協議。 如果已判斷出協議，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]尚未定義的兩個交易夥伴之間的協議屬性不會使用後援協議的屬性值。  
  
 如果連接埠設定需要驗證，就不會使用後援協議。 如果接收埠的通訊埠設定需要驗證 (如果有任一個**驗證失敗時捨棄訊息**或**驗證失敗時保留訊息**上選取了 **一般**頁面**接收埠屬性**對話方塊)，都需要接收埠收到的任何交換的協議。 在此情況下，不會使用後援協議。 如果沒有協議由決定的交換，交換會被視為驗證失敗，而且不會擱置。  
  
## <a name="see-also"></a>另請參閱  
 [協議解析、 結構描述探索和授權的收到的 EDI 訊息](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)   
 [協議解析和外寄 EDI 訊息的結構描述判斷](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md)   
 [設定 EDI 屬性](../core/configuring-edi-properties.md)   
 [設定全域或後援協議屬性](../core/configuring-global-or-fallback-agreement-properties.md)   
 [EDI 合作對象的已知的問題](../core/known-issues-with-edi-parties.md)
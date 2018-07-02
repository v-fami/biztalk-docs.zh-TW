---
title: 如何匯入 EDI-AS2 解決方案的繫結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3b918fa2-44f2-4f57-95af-36858cea0d86
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf69082ccc2e41ff16959b7b2399d3a45759fc3f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967848"
---
# <a name="how-to-import-bindings-for-an-edi-as2-solution"></a>如何匯入 EDI-AS2 解決方案的繫結
本主題說明如何將 EDI 和 (或) AS2 方案的組態匯入至另一部電腦。 EDI/AS2 方案的部署會與 BizTalk 應用程式部署整合， 因此您可以透過 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台和 BTSTask 命令列工具來進行部署。  
  
 您可以匯入的組態[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用您建立來源電腦透過匯出適當繫結的繫結檔案。 如需匯出至繫結檔案的組態資訊，請參閱 <<c0> [ 如何匯出 EDI-AS2 解決方案的繫結](../core/how-to-export-bindings-for-an-edi-as2-solution.md)。 從組態建立的繫結檔案的相關資訊，請參閱[繫結檔案的結構](../core/structure-of-a-binding-file.md)。  
  
 您也可以使用 .msi 檔，隨著匯入應用程式一併匯入繫結。 如需詳細資訊，請參閱 <<c0> [ 如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。 或者，您可以使用 BTSTask 命令匯出和匯入繫結。 如需 BTSTask 的詳細資訊，請參閱[BTSTask 命令列參考](../core/btstask-command-line-reference.md)中的主題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
## <a name="prerequisites"></a>必要條件  
  
- 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組成員的帳戶來登入。 如需詳細資訊，請參閱 <<c0> [ 部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
- 您必須新增的參考**BizTalk EDI 應用程式**從 BizTalk 應用程式將用於做為 EDI 應用程式。 如需將參考加入 BizTalk EDI 應用程式的指示，請參閱 <<c0> [ 如何將參考加入 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。  
  
## <a name="importing-bindings"></a>匯入繫結  
 當您匯入組態時，將會覆寫現有的 [EDI 屬性]。 如果您要將屬性匯入具有相同名稱的現有合作對象的合作對象[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會覆寫的 EDI 屬性 （或任何繫結） 的現有合作對象。 此外，如果您要匯入 EDI 全域屬性，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將會覆寫現有的 EDI 全域屬性。  
  
 匯入組態之後，您必須重新設定密碼。 基於安全性理由，當您匯出繫結檔案，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]從檔案移除繫結密碼。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ISA1、 ISA2、 ISA3 和 ISA4 欄位從 X12 與 EDIFACT 屬性移除 UNB6.1 和 UNB6.2 欄位屬性。 匯入繫結之後，您必須重新設定這些機密欄位，才能處理 EDI 訊息。  
  
 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]無法匯入一組繫結，原因可能是受信任的主控件屬性繫結檔案中是不同於主應用程式的信任的驗證屬性。 您可以變更繫結檔中的 Host Trusted 屬性來解決此問題。  
  
> [!NOTE]
>  從舊版的 BizTalk Server 將繫結檔案匯入到 BizTalk Server 可能會失敗。 夥伴管理模型已大幅變更，以便讓 BizTalk Server，因為從舊版 BizTalk Server 匯入繫結檔案不能建立實體 BizTalk Server 中根據新的模型。 如需詳細資訊，請參閱 <<c0> [ 如何在上一個 BizTalk Server 版本轉譯的合作對象定義成新的 TPM 實體？](../core/how-to-import-bindings-for-an-edi-as2-solution.md#BKMK_Party)。  
  
### <a name="to-import-the-configuration-from-a-binding-file"></a>從繫結檔匯入組態  
  
1. 您想要匯入若要開啟 設定在電腦上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 以滑鼠右鍵按一下您想要匯入成 EDI/AS2 組態，指向 BizTalk 應用程式**匯入**，然後按一下**繫結**。  
  
3. 在匯入繫結 對話方塊中，移至包含您的繫結檔案的位置，然後按一下**開啟**。  
  
4. 在匯入繫結之後, 開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 手動將所有 EDI 密碼欄位設定為適當的值。  
  
##  <a name="BKMK_Party"></a> 如何做在前一個 BizTalk Server 版本轉譯的合作對象定義成新的 TPM 實體？  
 在 BizTalk Server 合作對象定義會是基本上協議定義兩個交易夥伴之間交換訊息的方式。 在 BizTalk Server、 EDI 和 AS2 傳訊經過許多變更和新的交易夥伴管理 (TPM) 模型現在需要兩個交易的商務設定檔之間建立協議。 因此，基本上，存在於協議，必須先定義兩個交易夥伴，同時交易夥伴設定檔和通訊協定設定這兩個交易商務設定檔。 一旦您已定義這些實體，您可以建立交易夥伴協議。  
  
> [!NOTE]
>  如相關 TPM BizTalk Server 中的增強功能的詳細資訊，請參閱[交易夥伴管理解決方案的建置組塊](../core/building-blocks-of-a-trading-partner-management-solution.md)。  
  
 指定新的 TPM 物件模型，這代表您建立在 BizTalk Server EDI 應用程式，無法移轉至 BizTalk Server？ 答案是沒有。 您可以使用合作對象移轉工具從舊版 BizTalk Server 移轉合作對象資料，以重複使用現有的應用程式，從 BizTalk Server 2006 R2 或 BizTalk Server 中的 BizTalk Server 2009。 如需有關此工具的詳細資訊，請參閱[移轉 EDI 成品從 BizTalk Server 先前版本](http://msdn.microsoft.com/library/b956a97e-03d0-47ea-a2ce-c07a339c0f2c)。  
  
## <a name="see-also"></a>另請參閱  
 [匯入繫結](../core/importing-bindings2.md)
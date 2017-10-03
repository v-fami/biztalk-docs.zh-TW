---
title: "安裝、 設定及部署 EDI 和 AS2 解決方案的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dee03f0-2447-4cc2-90f4-e9b73caa0f39
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 406e69cafd4822a0f8f436b471d53c4e815dce32
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-installation-configuration-and-deployment-of-edi-and-as2-solutions"></a>安裝、組態及部署 EDI 和 AS2 解決方案的已知問題
本主題描述部署和管理方面的已知的問題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI 和 AS2 解決方案。  
  
## <a name="blank-strings-were-imported-for-party-properties"></a>針對合作對象屬性匯入空白字串  
 **徵兆**  
  
 當您從繫結檔將 EDI/AS2 繫結匯入至 BizTalk 應用程式時，並不會匯入機密的合作對象屬性，例如密碼或安全性/驗證資訊。 這些屬性會設為空白字串。  
  
 **可能的原因**  
  
 BizTalk Server 不會匯入這些機密欄位的設定。 匯入這些設定可能製造安全性問題。  
  
 **解決方式**  
  
 您必須在將繫結匯入至另一部電腦之後，手動設定 EDI 機密欄位的值。  
  
## <a name="ftp-adapter-is-not-supported-natively-in-64-bit-mode"></a>64 位元模式本身不支援 FTP 配接器  
 FTP 配接器無法以原生 64 位元模式執行。 如果您使用 FTP 配接器中的 EDI 解決方案中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您必須在 64 位元 Windows 上 WOW64 上執行它。  
  
## <a name="some-edias2-artifacts-are-still-active-after-unconfiguring"></a>一些 EDI/AS2 成品在取消設定後依然在作用中  
 您取消設定 Microsoft EDI/AS2 功能之後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，某些與 EDI 和 AS2 處理相關的 BizTalk Server 成品仍會在 BizTalk 群組組態的內容中使用。 這些成品將會包括 EDI 和 AS2 管線，以及批次協調流程。 因此，即使在取消設定 Microsoft EDI/AS2 功能後，您依然能夠執行基本的 EDI 和 AS2 處理。 若要停用此功能，您應停用、停止或刪除與 EDI 和 AS2 處理相關的連接埠。  
  
## <a name="you-receive-the-error-failed-to-configure-edias2-status-reporting-functionalities"></a>您會收到 「 無法設定 EDI/AS2 狀態報告功能 」 錯誤  
 **徵兆**  
  
 設定「EDI/AS2 Runtime 狀態報告」時，您收到「無法設定 EDI/AS2 狀態報告功能」錯誤。  
  
 **可能的原因**  
  
 如果您之前設定了 [BAM 工具] 然後解除設定，就可能會收到此錯誤。  
  
 **解決方式**  
  
 請在設定 EDI 和 (或) AS2 狀態報告之前，先設定 [BAM 工具]。  
  
## <a name="recovering-a-deleted-artifact-from-the-biztalk-edi-application-requires-you-to-reconfigure-the-edias2-runtime"></a>復原刪除的成品從 「 BizTalk EDI 應用程式會要求您重新設定 EDI/AS2 執行階段  
 您應避免針對自己的成品使用 BizTalk EDI 應用程式。 此應用程式包含 EDI/AS2 設定期間部署的 EDI/AS2 成品。 建議的方法是建立另一個應用程式，並且新增 BizTalk EDI 應用程式的參考至您的應用程式。 不過，如果您從 BizTalk EDI 應用程式刪除任何 EDI/AS2 成品，可透過在群組中的每部執行階段電腦上取消設定 BizTalk EDI/AS2 執行階段 (或是透過從群組取消設定 EDI/AS2 執行階段，以及在每一部可存取的執行階段電腦上取消設定 EDI/AS2 執行階段) 的方式從該狀態復原。 建議您不要刪除資料庫或 EDI/AS2 BAM 活動，以避免資料遺失。 然後，您可以在群組中的所有執行階段電腦上重新設定 EDI/AS2 執行階段，以復原刪除的 EDI/AS2 成品。  
  
## <a name="numeric-transaction-set-group-control-and-interchange-control-values-may-be-truncated"></a>數字的交易集、 群組控制項和交換控制項的值可能被截斷  
 交易集參考編號的交換控制編號值範圍欄位，以及群組控制編號可讓您輸入超過最大允許值的值。 當您儲存設定時，這些值會被截斷的最大值。  
  
 X12 的最大值屬性欄位是 999999999。  
  
 EDIFACT 屬性欄位的最大值是 99999999999999。  
  
## <a name="control-numbers-are-reset-to-1-after-upgrade"></a>控制編號重設為 1 之後升級  
 在升級之後，您可能會注意到所有顯示的合作對象的 EDI 內容中的控制編號重設的預設最小值為 1，並顯示 999999999 (X12) 或 99999999999999 (EDIFACT) 的預設最大值。 任何前置詞或後置詞的值會在升級之後維持相同。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]顯示用於控制編號的最小和最大值。 升級; 期間，將保留目前的控制編號不過它不會顯示合作對象的 EDI 屬性中。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解 EDI 和 AS2 解決方案](../core/troubleshooting-edi-and-as2-solutions.md)   
 [BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)   
 [BizTalk Server 2013 和 2013 R2 設定概觀](http://msdn.microsoft.com/library/aa58c43f-8f0e-4a5c-89b9-db7b8a852a72)   
 [環境最佳化的後續設定步驟](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md)
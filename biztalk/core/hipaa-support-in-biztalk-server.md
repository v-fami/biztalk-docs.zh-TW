---
title: BizTalk Server 中的 HIPAA 支援 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1ad8c64-6375-4364-80ce-440db943c222
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7817e3b69edd0a34c13b92128f7ddba0f28a5586
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014759"
---
# <a name="hipaa-support-in-biztalk-server"></a>BizTalk Server 中的 HIPAA 支援
本主題提供 HIPAA 和 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] 如何支援 HIPAA 的簡短概觀。  
  
## <a name="introduction-to-hipaa"></a>HIPAA 簡介  
 根據 1996 年的健康保險流通與責任法案 (HIPAA) 規定，受規範的實體在透過電子方式執行交易 (如理賠、匯款、合格性、理賠狀態要求與回應等等) 時，必須達到所規定的標準。 HIPAA 下規範的實體包括健保計畫、票據交換所與大部分的醫療保健業者。  
  
## <a name="hipaa-support-in-biztalk-server"></a>BizTalk Server 中的 HIPAA 支援  
 Microsoft 一向致力於協助醫療保健相關組織改善醫療保健服務的提供與財務情況。 Microsoft 矢志要降低這些組織為符合 HIPAA 法規所需花費的時間與金錢。  
  
 組織面臨需要綜合各種醫療保健系統來建立自動化商務程序的挑戰，但是有了 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，他們將能克服這項挑戰。 受 HIPAA 規範的組織可使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的功能，來開發、實作及整合既與交易相容、又符合聯邦法律的解決方案。  
  
[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] 所包含的原生功能可提供 HIPAA 的支援。 這項功能不是產品的增益集 (例如配接器或加速器)， 它已經內建於產品中。 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] 所包含的 EDI 元件與功能，不僅能協助組織符合 HIPAA 法規，還能夠真正將 HIPAA 的精髓融入商務程序，以建立管理縝密、講求數據的商務程序。  
  
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] 支援 HIPAA 5010 和 4010 版。  
  
## <a name="hipaa-documentation-in-biztalk-server"></a>BizTalk Server 中的 HIPAA 文件  
 主要的 EDI 標準是 X12 (由 ANSI 制定標準，主要用於北美洲) 及 EDIFACT (由聯合國制定標準，主要用於美國以外的地區)。 HIPAA 是衍生自 X12 的標準。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的原生 X12 EDI 功能中已經提供了 HIPAA 支援。 因此，只要您在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 文件中讀到 X12 支援，除非另有指明，否則該支援同樣也適用於 HIPAA 處理。  
  
 下列各節中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]的 HIPAA 的特定資訊。  
  
 **快速入門**  
  
- [HIPAA 交易集](../core/hipaa-transaction-sets.md)  
  
  **規劃和架構**  
  
- [HIPAA 文件結構描述版本 5010](../core/hipaa-document-schema-version-5010.md)  
  
- [HIPAA 結構描述觸發欄位註解](../core/hipaa-schema-trigger-field-annotations.md)  
  
- [分割 HIPAA 子文件](../core/splitting-hipaa-subdocuments.md)  
  
  **開發**  
  
- [修改 EDI 結構描述](../core/modifying-edi-schemas.md) 

- [在信封結構描述中自訂列舉](../core/customizing-enumerations-in-the-envelope-schema.md)

- [設定欄位交互驗證](../core/configuring-cross-field-validation.md)

  
 **疑難排解**  
  
-   [EDI 接收處理的已知問題](../core/known-issues-with-edi-receive-processing.md)  
  
-   [與 EDI 解決方案搭配使用之 XML 工具的已知問題](../core/known-issues-with-xml-tools-used-with-edi-solutions.md)  
  
## <a name="more-information-about-hipaa"></a>HIPAA 的相關資訊  
  
-   如需 American National Standards Institute，Accredited Standards Committee for Electronic Data Interchange，請移至[ASC X12 首頁](http://www.x12.org/)。  
  
-   如需 x12's Insurance Subcommittee 及其實作的資訊引導 HIPAA 下採用，請移至[Washington Publishing Company's HIPAA EDI 引導](http://www.wpc-edi.com/)。
  
-   如需 Workgroup for Electronic Data Interchange 資訊，請移至[Workgroup for Electronic Data Interchange 首頁](http://www.wedi.org/)。
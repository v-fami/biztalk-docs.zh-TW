---
title: "EDI 字元集支援 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4f4492b-8cbe-48ed-810a-3e73e1cb5996
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c1463d8a06ab5da89306aababfe19362d6308dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="edi-character-set-support"></a>EDI 字元集支援
本主題說明中的 EDI 功能支援字元集[!INCLUDE[prague](../includes/prague-md.md)]。  
  
|EDI 編碼|支援的字元集|  
|------------------|------------------------------|  
|X12 （包括 HIPAA）|X12 - 基本字元集 (ASCII 的子集)|  
|-|X12- 擴充的字元集 (ASCII 的子集，同時包含 ISO8859-1 字元)|  
|-|UTF8/UNICODE|  
|EDIFACT|UNOA|  
|-|UNOB|  
|-|UNOC-ISO 8859-1： 資訊處理-第 1 部分： 拉丁字母 [否]。 1|  
|-|KECA - KS_C_5601-1987 (Windows 949 字碼頁)|  
|-|UNOX (ISO2022 – JP)|  
|-|UNOY-UTF8 編碼資料**附註：** UNOD 到 UNOK 字元集設定的支援 UTF8 編碼的資料也支援。|  
  
## <a name="setting-the-edi-character-set"></a>設定 EDI 字元集  
 對於 X12 編碼交換，您可以設定 CharacterSet 管線屬性，來設定管線的字元集。 如需詳細資訊，請參閱[設定 EDI 管線屬性](../core/configuring-edi-pipeline-properties.md)。  
  
> [!NOTE]
>  在 [BizTalk Server 管理主控台] 中，[X12 EDI 屬性] 對話方塊的 [產生 X12 交換信封] 頁面上有一個 X12 字元集控制項，但該控制項只是用來驗證 [EDI 屬性] 對話方塊中的屬性輸入值。  
  
 對於 EDIFACT 編碼交換，您可以在 [做為交換接收者的合作對象] 的 [UNB 區段定義] 屬性頁中設定 UNB1.1 合作屬性，來設定合作對象的字元集。 內送交換中使用的編碼，則由交換之標頭內的 UNB1.1 欄位值決定。 如需詳細資訊，請參閱[設定信封 （EDIFACT 交易集設定）](../core/configuring-envelopes-edifact-transaction-set-settings.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定 EDI 管線屬性](../core/configuring-edi-pipeline-properties.md)   
 [設定信封 （EDIFACT 交易集設定）](../core/configuring-envelopes-edifact-transaction-set-settings.md)
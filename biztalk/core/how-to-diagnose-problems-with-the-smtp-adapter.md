---
title: 如何診斷 SMTP 配接器的問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eaf39fd8-b662-4b0c-b5e8-1af02cb4f79b
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5a1f88d6d096b697f8fceb3c81f8527fa5f7342
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010311"
---
# <a name="how-to-diagnose-problems-with-the-smtp-adapter"></a>如何診斷 SMTP 配接器問題
本節包含的步驟可協助您診斷 SMTP 配接器的問題。  
  
### <a name="check-the-smtp-log-files-of-the-smtp-server-for-errors"></a>檢查 SMTP 伺服器的 SMTP 記錄檔是否出現錯誤  
  
- SMTP 伺服器記錄檔包含的資訊，可協助您疑難排解 SMTP 配接器的問題。 根據預設，[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 上的 SMTP 記錄檔位於下列目錄：  
  
   <em>%Windir%\\</em>system32\LogFiles\SMTPSVC1\  
  
  > [!NOTE]
  >  *%Windir%* 是 SMTP 伺服器上的 Windows 目錄位置的預留位置。  
  > 
  > [!NOTE]
  >  SMTP 記錄功能預設為停用上[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]。 如需啟用 SMTP 記錄功能的詳細資訊，請參閱 Windows Server 文件。  
  
## <a name="see-also"></a>另請參閱  
 [工具和公用程式來使用，以進行疑難排解](../core/tools-and-utilities-to-use-for-troubleshooting.md)   
 [SMTP 配接器疑難排解](../core/troubleshooting-the-smtp-adapter.md)
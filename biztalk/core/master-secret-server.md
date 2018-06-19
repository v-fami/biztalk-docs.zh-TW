---
title: 主要密碼伺服器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Master Secret server, about Master Secret server
- Master Secret server, SSO
- SSO, encryption key
- Master Secret server, encryption key
- SSO, Master Secret server
ms.assetid: 93685a19-6c27-45db-bfc1-957574362687
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d02d5608546e86801bfc4a2281c42f902594e79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262510"
---
# <a name="master-secret-server"></a>主要密碼伺服器
主要密碼伺服器是儲存主要密碼 (加密金鑰) 的企業單一登入 (SSO) 伺服器。 主要密碼伺服器會於 SSO 系統管理員要求時產生主要密碼。 而且主要密碼伺服器會將加密的主要密碼儲存在登錄中。 只有「單一登入」系統管理員可以存取主要密碼。  
  
 其他的單一登入伺服器會每隔 30 秒查看主要密碼是否有變更。 若它已變更，伺服器就會以安全的方式讀取它，否則會繼續使用已快取於記憶體中的主要密碼。 SSO 服務會使用主要密碼，來加密和解密使用者認證。  
  
 除非 SSO 系統管理員設定主要密碼伺服器並產生主要密碼，否則您將無法使用 SSO 系統。 主要密碼伺服器會在設定組態期間產生主要密碼。 只有 SSO 系統管理員可以產生主要密碼。 SSO 系統管理員必須設定主要密碼伺服器及 SSO 資料庫，應用程式才可以使用 SSO 服務。  
  
> [!IMPORTANT]
>  在您產生主要密碼之後，強烈建議您備份它，並將它儲存在安全的位置。  
  
 當 SSO 系統管理員需要重新產生主要密碼時 (例如，若 SSO 系統管理員想要定期變更主要密碼)，主要密碼伺服器會同時儲存舊的與新的主要密碼。 主要密碼伺服器接著會查看所有的對應、使用舊的主要密碼將之解密，並使用新的主要密碼再次將它們加密。  
  
 若主要密碼伺服器失敗，所有已經在執行的執行階段作業都將繼續執行，但是 SSO 伺服器將無法加密新認證。  
  
> [!IMPORTANT]
>  SSO 系統中只能有一台主要密碼伺服器。 因此，強烈建議您建立主要密碼伺服器叢集。 如需詳細資訊，請參閱[如何叢集化主要密碼伺服器](../core/how-to-cluster-the-master-secret-server1.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 SSO](../core/using-sso.md)
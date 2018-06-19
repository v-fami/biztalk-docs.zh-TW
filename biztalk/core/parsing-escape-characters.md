---
title: 剖析逸出字元 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], code samples
- pipeline components [custom], escape characters
- pipeline components [custom], parsing
ms.assetid: 2b33f436-3c29-4ff5-8dfa-26d6591713bc
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f200e7c68a43360dc9edbae42ebea196b884f577
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971972"
---
# <a name="parsing-escape-characters"></a><span data-ttu-id="a9660-102">剖析逸出字元</span><span class="sxs-lookup"><span data-stu-id="a9660-102">Parsing Escape Characters</span></span>
<span data-ttu-id="a9660-103">當剖析器碰到在一般字元 (也就是非分隔符號或其他特殊字元) 之前的逸出字元時，便會忽略逸出字元。</span><span class="sxs-lookup"><span data-stu-id="a9660-103">When the parser encounters an escape character that prefixes a regular character (that is, one that is not a delimiter or other special character), the escape character is ignored.</span></span> <span data-ttu-id="a9660-104">例如，其中指定字串"abc\d""\\"是逸出字元的輸出是"abcd"。</span><span class="sxs-lookup"><span data-stu-id="a9660-104">For example, given a string "abc\d" where "\\" is the escape character, the output is "abcd".</span></span>  
  
 <span data-ttu-id="a9660-105">如果剖析器碰到雙逸出字元 (例如，"abc\\\d")，輸出會包含單一的逸出字元 ("abc\d")。</span><span class="sxs-lookup"><span data-stu-id="a9660-105">If the parser encounters a double escape character (for example, "abc\\\d"), the output includes a single escape character ("abc\d").</span></span>  
  
 <span data-ttu-id="a9660-106">如果剖析器碰到三個逸出字元 (例如，abc\\\\\d)，輸出會是"abc\d"，因為前兩個逸出字元會被剖析為"\\」，第三個逸出字元會被忽略。</span><span class="sxs-lookup"><span data-stu-id="a9660-106">If the parser encounters three escape characters (for example, abc\\\\\d), the output is "abc\d" because the first two escape characters are parsed to "\\" and the third escape character is ignored.</span></span>  
  
 <span data-ttu-id="a9660-107">剖析器會將誤置的分隔符號視為一般字元。</span><span class="sxs-lookup"><span data-stu-id="a9660-107">The parser treats misplaced delimiters as regular characters.</span></span> <span data-ttu-id="a9660-108">例如，如果收到 「 資料錄，Field1，Field，2"，輸出 XML 是\<Field1\> \<Field，2\>。</span><span class="sxs-lookup"><span data-stu-id="a9660-108">For example, if "Record, Field1, Field,2" is received, the output XML is \<Field1\> \<Field,2\>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9660-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="a9660-109">See Also</span></span>  
 [<span data-ttu-id="a9660-110">使用一般檔案剖析引擎</span><span class="sxs-lookup"><span data-stu-id="a9660-110">Using the Flat File Parsing Engine</span></span>](../core/using-the-flat-file-parsing-engine.md)
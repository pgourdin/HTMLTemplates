It's interesting to see the interaction of the various markdown text effects that you can do. We have *italic (i)*, __bold (b)__, ==highlighted (h)==, ~~strikethrough (s)~~, and `code (c)`. I first tried all of the permutations of the first four, just to make sure that they were all compatible and nest-able.

outer *i __b ==h ~~s inner s~~ h== b__ i* outer
outer *i __b ~~s ==h inner h== s~~ b__ i* outer
outer *i ==h __b ~~s inner s~~ b__ h== i* outer
outer *i ==h ~~s __b inner b__ s~~ h== i* outer
outer *i ~~s __b ==h inner h== b__ s~~ i* outer
outer *i ~~s ==h __b inner b__ h== s~~ i* outer
outer __b *i ==h ~~s inner s~~ h== i* b__ outer
outer __b *i ~~s ==h inner h== s~~ i* b__ outer
outer __b ==h *i ~~s inner s~~ i* h== b__ outer
outer __b ==h ~~s *i inner i* s~~ h== b__ outer
outer __b ~~s *i ==h inner h== i* s~~ b__ outer
outer __b ~~s ==h *i inner i* h== s~~ b__ outer
outer ==h *i __b ~~s inner s~~ b__ i* h== outer
outer ==h *i ~~s __b inner b__ s~~ i* h== outer
outer ==h __b *i ~~s inner s~~ i* b__ h== outer
outer ==h __b ~~s *i inner i* s~~ b__ h== outer
outer ==h ~~s *i __b inner b__ i* s~~ h== outer
outer ==h ~~s __b *i inner i* b__ s~~ h== outer
outer ~~s *i __b ==h inner h== b__ i* s~~ outer
outer ~~s *i ==h __b inner b__ h== i* s~~ outer
outer ~~s __b *i ==h inner h== i* b__ s~~ outer
outer ~~s __b ==h *i inner i* h== b__ s~~ outer
outer ~~s ==h *i __b inner b__ i* h== s~~ outer
outer ~~s ==h __b *i inner i* b__ h== s~~ outer

I then threw in `code (c)` to see what compatibilities existed with it and the other four. The results are interesting. Of course, any markdown special characters within the context of `code` is rendered literally (as best exemplified in the last lines, below). What's surprising is that ==highlighting== and `code` do not play nice together. `Code` content nested in *italic*, __bold__ and ~~strikethrough~~ retain those formats, but ==highlighted== does not. You can see this best in the third line, below. But, also note that the red text of `code` formatting is lost as well.

outer *i __b ==h ~~s `c inner c` s~~ h== b__ i* outer
outer *i __b ==h `c ~~s inner s~~ c` h== b__ i* outer
outer *i __b ~~s ==h `c inner c` h== s~~ b__ i* outer
outer *i __b ~~s `c ==h inner h== c` s~~ b__ i* outer
outer *i __b `c ==h ~~s inner s~~ h== c` b__ i* outer
outer *i __b `c ~~s ==h inner h== s~~ c` b__ i* outer
outer *i ==h __b ~~s `c inner c` s~~ b__ h== i* outer
outer *i ==h __b `c ~~s inner s~~ c` b__ h== i* outer
outer *i ==h ~~s __b `c inner c` b__ s~~ h== i* outer
outer *i ==h ~~s `c __b inner b__ c` s~~ h== i* outer
outer *i ==h `c __b ~~s inner s~~ b__ c` h== i* outer
outer *i ==h `c ~~s __b inner b__ s~~ c` h== i* outer
outer *i ~~s __b ==h `c inner c` h== b__ s~~ i* outer
outer *i ~~s __b `c ==h inner h== c` b__ s~~ i* outer
outer *i ~~s ==h __b `c inner c` b__ h== s~~ i* outer
outer *i ~~s ==h `c __b inner b__ c` h== s~~ i* outer
outer *i ~~s `c __b ==h inner h== b__ c` s~~ i* outer
outer *i ~~s `c ==h __b inner b__ h== c` s~~ i* outer
outer *i `c __b ==h ~~s inner s~~ h== b__ c` i* outer
outer *i `c __b ~~s ==h inner h== s~~ b__ c` i* outer
outer *i `c ==h __b ~~s inner s~~ b__ h== c` i* outer
outer *i `c ==h ~~s __b inner b__ s~~ h== c` i* outer
outer *i `c ~~s __b ==h inner h== b__ s~~ c` i* outer
outer *i `c ~~s ==h __b inner b__ h== s~~ c` i* outer
outer __b *i ==h ~~s `c inner c` s~~ h== i* b__ outer
outer __b *i ==h `c ~~s inner s~~ c` h== i* b__ outer
outer __b *i ~~s ==h `c inner c` h== s~~ i* b__ outer
outer __b *i ~~s `c ==h inner h== c` s~~ i* b__ outer
outer __b *i `c ==h ~~s inner s~~ h== c` i* b__ outer
outer __b *i `c ~~s ==h inner h== s~~ c` i* b__ outer
outer __b ==h *i ~~s `c inner c` s~~ i* h== b__ outer
outer __b ==h *i `c ~~s inner s~~ c` i* h== b__ outer
outer __b ==h ~~s *i `c inner c` i* s~~ h== b__ outer
outer __b ==h ~~s `c *i inner i* c` s~~ h== b__ outer
outer __b ==h `c *i ~~s inner s~~ i* c` h== b__ outer
outer __b ==h `c ~~s *i inner i* s~~ c` h== b__ outer
outer __b ~~s *i ==h `c inner c` h== i* s~~ b__ outer
outer __b ~~s *i `c ==h inner h== c` i* s~~ b__ outer
outer __b ~~s ==h *i `c inner c` i* h== s~~ b__ outer
outer __b ~~s ==h `c *i inner i* c` h== s~~ b__ outer
outer __b ~~s `c *i ==h inner h== i* c` s~~ b__ outer
outer __b ~~s `c ==h *i inner i* h== c` s~~ b__ outer
outer __b `c *i ==h ~~s inner s~~ h== i* c` b__ outer
outer __b `c *i ~~s ==h inner h== s~~ i* c` b__ outer
outer __b `c ==h *i ~~s inner s~~ i* h== c` b__ outer
outer __b `c ==h ~~s *i inner i* s~~ h== c` b__ outer
outer __b `c ~~s *i ==h inner h== i* s~~ c` b__ outer
outer __b `c ~~s ==h *i inner i* h== s~~ c` b__ outer
outer ==h *i __b ~~s `c inner c` s~~ b__ i* h== outer
outer ==h *i __b `c ~~s inner s~~ c` b__ i* h== outer
outer ==h *i ~~s __b `c inner c` b__ s~~ i* h== outer
outer ==h *i ~~s `c __b inner b__ c` s~~ i* h== outer
outer ==h *i `c __b ~~s inner s~~ b__ c` i* h== outer
outer ==h *i `c ~~s __b inner b__ s~~ c` i* h== outer
outer ==h __b *i ~~s `c inner c` s~~ i* b__ h== outer
outer ==h __b *i `c ~~s inner s~~ c` i* b__ h== outer
outer ==h __b ~~s *i `c inner c` i* s~~ b__ h== outer
outer ==h __b ~~s `c *i inner i* c` s~~ b__ h== outer
outer ==h __b `c *i ~~s inner s~~ i* c` b__ h== outer
outer ==h __b `c ~~s *i inner i* s~~ c` b__ h== outer
outer ==h ~~s *i __b `c inner c` b__ i* s~~ h== outer
outer ==h ~~s *i `c __b inner b__ c` i* s~~ h== outer
outer ==h ~~s __b *i `c inner c` i* b__ s~~ h== outer
outer ==h ~~s __b `c *i inner i* c` b__ s~~ h== outer
outer ==h ~~s `c *i __b inner b__ i* c` s~~ h== outer
outer ==h ~~s `c __b *i inner i* b__ c` s~~ h== outer
outer ==h `c *i __b ~~s inner s~~ b__ i* c` h== outer
outer ==h `c *i ~~s __b inner b__ s~~ i* c` h== outer
outer ==h `c __b *i ~~s inner s~~ i* b__ c` h== outer
outer ==h `c __b ~~s *i inner i* s~~ b__ c` h== outer
outer ==h `c ~~s *i __b inner b__ i* s~~ c` h== outer
outer ==h `c ~~s __b *i inner i* b__ s~~ c` h== outer
outer ~~s *i __b ==h `c inner c` h== b__ i* s~~ outer
outer ~~s *i __b `c ==h inner h== c` b__ i* s~~ outer
outer ~~s *i ==h __b `c inner c` b__ h== i* s~~ outer
outer ~~s *i ==h `c __b inner b__ c` h== i* s~~ outer
outer ~~s *i `c __b ==h inner h== b__ c` i* s~~ outer
outer ~~s *i `c ==h __b inner b__ h== c` i* s~~ outer
outer ~~s __b *i ==h `c inner c` h== i* b__ s~~ outer
outer ~~s __b *i `c ==h inner h== c` i* b__ s~~ outer
outer ~~s __b ==h *i `c inner c` i* h== b__ s~~ outer
outer ~~s __b ==h `c *i inner i* c` h== b__ s~~ outer
outer ~~s __b `c *i ==h inner h== i* c` b__ s~~ outer
outer ~~s __b `c ==h *i inner i* h== c` b__ s~~ outer
outer ~~s ==h *i __b `c inner c` b__ i* h== s~~ outer
outer ~~s ==h *i `c __b inner b__ c` i* h== s~~ outer
outer ~~s ==h __b *i `c inner c` i* b__ h== s~~ outer
outer ~~s ==h __b `c *i inner i* c` b__ h== s~~ outer
outer ~~s ==h `c *i __b inner b__ i* c` h== s~~ outer
outer ~~s ==h `c __b *i inner i* b__ c` h== s~~ outer
outer ~~s `c *i __b ==h inner h== b__ i* c` s~~ outer
outer ~~s `c *i ==h __b inner b__ h== i* c` s~~ outer
outer ~~s `c __b *i ==h inner h== i* b__ c` s~~ outer
outer ~~s `c __b ==h *i inner i* h== b__ c` s~~ outer
outer ~~s `c ==h *i __b inner b__ i* h== c` s~~ outer
outer ~~s `c ==h __b *i inner i* b__ h== c` s~~ outer
outer `c *i __b ==h ~~s inner s~~ h== b__ i* c` outer
outer `c *i __b ~~s ==h inner h== s~~ b__ i* c` outer
outer `c *i ==h __b ~~s inner s~~ b__ h== i* c` outer
outer `c *i ==h ~~s __b inner b__ s~~ h== i* c` outer
outer `c *i ~~s __b ==h inner h== b__ s~~ i* c` outer
outer `c *i ~~s ==h __b inner b__ h== s~~ i* c` outer
outer `c __b *i ==h ~~s inner s~~ h== i* b__ c` outer
outer `c __b *i ~~s ==h inner h== s~~ i* b__ c` outer
outer `c __b ==h *i ~~s inner s~~ i* h== b__ c` outer
outer `c __b ==h ~~s *i inner i* s~~ h== b__ c` outer
outer `c __b ~~s *i ==h inner h== i* s~~ b__ c` outer
outer `c __b ~~s ==h *i inner i* h== s~~ b__ c` outer
outer `c ==h *i __b ~~s inner s~~ b__ i* h== c` outer
outer `c ==h *i ~~s __b inner b__ s~~ i* h== c` outer
outer `c ==h __b *i ~~s inner s~~ i* b__ h== c` outer
outer `c ==h __b ~~s *i inner i* s~~ b__ h== c` outer
outer `c ==h ~~s *i __b inner b__ i* s~~ h== c` outer
outer `c ==h ~~s __b *i inner i* b__ s~~ h== c` outer
outer `c ~~s *i __b ==h inner h== b__ i* s~~ c` outer
outer `c ~~s *i ==h __b inner b__ h== i* s~~ c` outer
outer `c ~~s __b *i ==h inner h== i* b__ s~~ c` outer
outer `c ~~s __b ==h *i inner i* h== b__ s~~ c` outer
outer `c ~~s ==h *i __b inner b__ i* h== s~~ c` outer
outer `c ~~s ==h __b *i inner i* b__ h== s~~ c` outer
